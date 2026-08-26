# Google Search Console — Tenant-Level Default Site

*Shipped 2026-08-13, together with the GA4 tenant-level default property (backend issue #590).*

## Why

Every Google Search Console data call used to require the caller to pass a `siteUrl`:

- `POST /custom-report` — body field
- `POST /url-inspection` — body field (was even `@NotBlank`)
- `GET /sitemaps` — mandatory query parameter

A Google account often has several verified sites (agency accounts especially), but a GoodBards tenant almost always works against **one** of them. Forcing every caller — frontend, AI agents, external API consumers — to discover, store, and resend the site on each request duplicated state in every consumer and made "which site is this tenant's?" a question with no authoritative answer.

The evolution: the tenant's default site is now **part of the connector configuration**, and every endpoint falls back to it. The same pattern was applied to Google Analytics (`propertyId`/`propertyName`) the same day.

## What changed — at a glance

| | Before | After |
|---|---|---|
| Source of truth for the site | Each caller | Connector config (`siteUrl`, per tenant) |
| `GET /config` | OAuth state only | OAuth state **+ `siteUrl`** |
| `POST /custom-report` | `siteUrl` required in body | Optional — falls back to tenant default |
| `POST /url-inspection` | `siteUrl` required (`@NotBlank`) | Optional — falls back to tenant default |
| `GET /sitemaps` | `?siteUrl=` required (400 if missing) | Optional — falls back to tenant default |
| AI agent (`querySearchAnalytics`) | Fails unless `selectSearchConsoleSite` was called in the session | Session selection → tenant default → error |
| Choosing the site | Nowhere in the product | Connections → Google Search Console → **Manage Configuration** |
| After OAuth connect | No site anywhere | First verified site auto-saved as default |

## The configuration contract

`GET /v1/{tenant-id}/integrations/google-search-console/config` now returns:

```json
{
  "active": true,
  "username": "alan@goodbards.com",
  "profileUrl": "https://lh3.googleusercontent.com/...",
  "siteUrl": "https://www.goodbards.com/"
}
```

`siteUrl` accepts both Search Console property forms:

- URL-prefix property: `https://www.example.com/`
- Domain property: `sc-domain:example.com`

It is set via `POST .../save-config`, and the valid values come from `GET .../accounts` (the connected account's verified sites).

**Fill-only semantics** — a `save-config` that *omits* `siteUrl` (e.g. the OAuth token-refresh/reconnect payload) does **not** wipe the stored value. Only an explicit value overwrites it. This is what makes reconnecting safe.

## Site resolution — one rule everywhere

Every data endpoint resolves the effective site the same way:

```
explicit siteUrl in the request        (always wins)
        ↓ not provided
tenant's configured default site       (from connector config)
        ↓ not configured
400 INVALID_PARAMETER                  (structured GoodBardsError)
```

So existing callers that pass `siteUrl` explicitly are **unchanged**, and new callers can simply omit it.

The AI agent tool adds one tier on top: a site selected in the conversation (`selectSearchConsoleSite`, stored as the session variable `gscSiteUrl`) overrides the tenant default for that session. An agent can now answer "how did our search clicks do last week?" with zero setup — it no longer errors with *"No site selected"* when the tenant has a default.

## How it is stored

Connector configuration is key/value parameter rows, so the change is one new parameter definition — no new table, no new column:

```sql
INSERT INTO C_INFRA_PARAMS (uid, label, type, multivalued) VALUES
('00000000-0000-0000-0000-000000000152', 'siteUrl', 'STRING', false)
ON CONFLICT DO NOTHING;

INSERT INTO C_INFRA_INTEGRATIONS_PARAMS(connector_id, param_uid, description, default_value, required) VALUES
('google-search-console', '00000000-0000-0000-0000-000000000152', 'siteUrl', '', false)
ON CONFLICT DO NOTHING;
```

- Migration for existing databases: `common-config/src/main/db/migrations/2026-08-13-gsc-site-url-config.sql` (idempotent, safe to re-run).
- Seed for fresh bring-ups: `02-infra-connectors.sql`.
- GA4's equivalent fields are `...150` (`propertyId`) and `...151` (`propertyName`). GSC needs only one field because a Search Console site has no display name — **the URL is the name**.

## Architecture note: the Google base class became generic

To give GSC its own configuration type without duplicating OAuth code, the shared base class evolved:

```
Before:  AbstractGoogleIntegrationService  (hardcoded to GoogleConfiguration)
After:   AbstractGoogleIntegrationService<CONFIG extends GoogleConfiguration>
```

- The base keeps all OAuth machinery (token info, refresh, form encoding) — untouched.
- A new `newConfiguration()` factory lets each connector produce its own config type.
- `GoogleSearchConsoleServices` extends it with `GoogleSearchConsoleConfiguration` and overrides the two `mapConfiguration` methods, calling `super` for the shared fields and adding `siteUrl` (fill-only on write, optional on read so pre-existing tenants without the key don't break).
- The five other Google connectors (YouTube, Ads, Trends, Documents, Drive) took a one-line type change: `extends AbstractGoogleIntegrationService<GoogleConfiguration>`.

This also unblocks the standing tech-debt item: Google Analytics still duplicates the OAuth layer instead of using this base class — it can now be folded back in, since the base supports per-connector config types.

## Product surface

- **Connections page** — the GSC card, when connected, shows **Manage Configuration**: a modal listing the account's verified sites (URL + permission level) to pick the tenant default.
- **OAuth connect** — right after a successful connect, the first verified site is saved as the default automatically. This only happens when no default exists yet, so reconnecting never overwrites a deliberate choice.
- Legacy tenants (connected before this change) simply have no `siteUrl` in config until they pick one — every endpoint then behaves exactly as before (explicit siteUrl required).

## Rollout & compatibility

1. Run the migration (above) — additive, idempotent.
2. Deploy the backend — all changes are backward compatible: explicit `siteUrl` still wins everywhere, and the response shapes are unchanged.
3. Deploy the frontend — adds the modal and OAuth defaulting; the save-config field is ignored by older backends only in the sense that it would be rejected as an unknown parameter, hence **backend first**.

One deliberate API relaxation to be aware of: `url-inspection` no longer rejects a missing `siteUrl` at the bean-validation layer (`@NotBlank` removed) and `sitemaps` no longer 400s on a missing query parameter — in both cases the tenant default is tried first, and the 400 (with a clear message) only happens when there is no default either.

## Related

- GA4 mirror of this change: tenant default property (`propertyId`/`propertyName`), tenant-level `custom-report` + `realtime-report`, and the daily summary email now reporting only the configured property.
- Test plan with ready-to-run curls: `frontend-v2/test-plans/2026-08-13-ga4-custom-report-endpoint.md` (Part C covers GSC).
