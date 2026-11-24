# Use the GoodBards API

Connect your own tools to GoodBards: push contacts from your website or CRM, and
pull campaigns and results into your own reports.

This guide is for the developer who writes the connection. It takes about an
hour for a first call.

## Before you start

- **An administrator.** Only a company administrator can create keys.
- **Your company ID.** Every call includes it (written `{tenant-id}` below). Ask
  support for it if you do not have it.

## 1. Create an API key

1. Open **Tenant Settings** from your account menu, then the **Security** tab.
2. Under **API Keys**, choose **Create API Key**.
3. Fill in:

    | Field | What to put |
    | --- | --- |
    | **Description** | What the key is for, for example *Website sign-up form*. |
    | **Scope** | **FULL** for the API, or **CHATBOT** for a key that only drives the website chatbot. |
    | **Restrict to a specific origin** | For a key used from a web page: the only website allowed to use it. |
    | **Expires at** | When the key stops working. Without a date, it lasts five years. |

4. Choose **Generate Key** and copy it into your tool's secret store.

The number of keys your plan allows is shown above the list.

!!! warning "Treat the key like a password"
    A FULL key reaches all of your company's data through the API, whoever
    created it. Keep it on a server, never in a web page or a mobile app, and
    give each integration its own key so you can revoke one without breaking the
    others.

## 2. Authenticate your requests

Send the key in the `Authorization` header:

```http
GET https://api.goodbards.ai/v1/{tenant-id}/campaigns
Authorization: Bearer <your API key>
```

Every path starts with `/v1/` and your company ID.

## 3. Common jobs

### Add a contact

```http
POST https://api.goodbards.ai/v1/{tenant-id}/cdp/contacts/
Authorization: Bearer <your API key>
Content-Type: application/json
```

!!! warning "A contact without a status is added as subscribed"
    Always send a status for people who did not agree to receive marketing
    emails. Only contacts with marketing consent should be **subscribed**; see
    [Adding contacts](../audience/adding-contacts.md).

To change some fields of a contact, use the call below
(**create or update by email**): only the fields you send change.

!!! warning "`PUT /cdp/contacts/{contact-id}` replaces the whole contact"
    It is the call the app's own edit form uses. Every field you leave out is
    emptied: names, phone, address, job title. Only the email, tags, status,
    `customFields`, `policies` and `companyIds` keep their value when you leave
    them out. Use it only after reading the full contact
    (`GET /v1/{tenant-id}/cdp/contacts/{contact-id}`) and sending it back with
    your changes.

### Sync contacts from your backend (create or update by email)

One call creates the contact, or updates it when the email is already there:

```http
PUT https://api.goodbards.ai/v1/{tenant-id}/cdp/contacts/by-email/{email}
Authorization: Bearer <your API key>
Content-Type: application/json

{
  "firstName": "Alice",
  "status": "regular",
  "customFields": { "quiz_archetype": "Titan" },
  "tagsAdd": ["status: customer"],
  "tagsRemove": ["path: A"]
}
```

- `201` = created, `200` = updated; the answer holds `created` and the contact.
- **Only what you send changes.** Tags are added and removed, never replaced;
  custom fields are merged (`null` clears one).
- **Tags start automations.** An added tag starts the **Tag added** automations
  and the stop rules within a minute, as a tag added in the app does. Adding
  `status: customer` stops a nurture flow with that stop rule before its next
  email.
- A new contact without a status is **subscribed**: send `regular` for people
  who did not agree to marketing emails.
- `GET .../cdp/contacts/by-email/{email}` reads a contact.
- A `400` lists every field it refused:

```json
{
  "message": "Some fields were not accepted",
  "errors": [
    { "field": "customFields.quiz_sid", "message": "not a contact custom field of this workspace" },
    { "field": "status", "message": "one of [do-not-contact, invalid-email, regular, subscribed, unsubscribed]" }
  ]
}
```

### List your campaigns

```http
GET https://api.goodbards.ai/v1/{tenant-id}/campaigns
```

### Read a campaign's results

| Call | What it does |
| --- | --- |
| `GET /v1/{tenant-id}/campaigns/{campaign-id}/analytics/reports` | Lists the campaign's reports. |
| `GET /v1/{tenant-id}/campaigns/{campaign-id}/analytics/reports/{report-id}` | Reads one report. |
| `POST /v1/{tenant-id}/campaigns/{campaign-id}/analytics/reports` | Starts a new report. It answers `202` at once; read it a little later. |

## 4. Errors

Errors come back with an HTTP status and a JSON body:

```json
{
  "code": "CONTACT_NOT_FOUND",
  "message": "Contact not found",
  "timestamp": "2026-10-11T09:30:00"
}
```

| Status | Usually means |
| --- | --- |
| `400` | Something in the request is missing or invalid; `code` says what. |
| `401` | The key is missing, wrong, revoked or expired. |
| `403` | The key may not do this, or a plan limit is reached. |
| `404` | The contact, campaign or report does not exist in your company. |
| `409` | The request conflicts with the current state, for example an email already used. |
| `5xx` | Our side. Retry later; if it persists, contact support with the time of the call. |

## 5. Revoke a key

On the same **Security** tab, open the key's menu and revoke it. Calls with that
key fail with `401` straight away.

## Good to know

- **One key per integration.** A leaked key is then one key to revoke.
- **Set an expiry date** and put a reminder in your calendar to renew it.
- **The full API reference** is available on request from support.

---

*Still stuck? [Contact support](../contact.md).*
