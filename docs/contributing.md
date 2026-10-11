# Documentation style guide

These docs are for **customers using GoodBards** — marketers, not engineers.
Everything below exists to keep 40+ pages sounding like one person wrote them.

## Who you are writing for

A marketing manager at an agency or mid-market company. They are smart, busy,
and not technical. They want to finish a task, not understand the system.

- Write **you**, not "the user".
- Use the words the UI uses. If the button says **Launch a Tactic**, never call
  it "initiating a tactic workflow".
- No internal vocabulary: no *tenant*, *sub-tenant*, *UID*, *endpoint*,
  *connector config*, *asset entity*. Say *your company*, *account*, *link*.
- Cut every sentence that does not help them finish the task.

## Page shape

Every feature page follows the same four headings, in this order:

| Heading | What goes in it |
| --- | --- |
| **What it's for** | 2–3 sentences on the problem it solves. |
| **Before you start** | Prerequisites. Delete the section if there are none. |
| **How to <task>** | Numbered steps matching the UI exactly. |
| **Good to know** | Limits, gotchas, and mistakes people actually make. |

Readers navigate by pattern. Do not invent new section names.

### Writing steps

- One action per numbered step.
- Bold every UI label exactly as it appears: choose **Save**, not click save.
- Say where things are: "In the sidebar, choose **Audience → Contacts**."
- Stop at the outcome: "Your contacts appear in the list."

## Screenshots

Screenshots carry more weight than prose for this audience, so they must look
consistent. The agreed convention:

| Setting | Value |
| --- | --- |
| Tenant | **Demo tenant only.** Never real customer data — this site is public. |
| Theme | **Light** |
| Viewport | **1440 × 900** |
| Format | PNG, saved to `docs/img/screenshots/<page-name>.png` |

Rules:

- **Never** screenshot a real customer's account. Names, email addresses,
  company names and metrics from a live tenant must not appear. PDPA applies.
- Screen pages: one screenshot unless a step is genuinely unclear without a
  second. Guides: one per stage is fine, placed right under the step it shows.
- Capture the relevant panel, not the whole desktop. Crop out the top bar: it
  shows the signed-in person's name and photo.
- Always write real alt text: `![The Contacts list with a segment applied](...)`.
  Screen-reader users and broken-image fallbacks both depend on it.
- Re-capture when the UI changes. A stale screenshot is worse than none.
- Every screenshot opens full size when clicked (glightbox). To opt one out, add
  `{ .no-lightbox }` after it.

### Animated GIFs

Use a GIF only when the movement *is* the instruction: dragging, an editor
interaction, a sequence a still image cannot show (for example inserting a field
in the email editor). Everything else stays a PNG.

- Same rules as screenshots: demo tenant, light theme, the panel only.
- Short: one action, under 10 seconds, no idle frames at the start or end.
- Under 2 MB. Save to `docs/img/gifs/<page-name>-<action>.gif`.
- Alt text says what happens: `![Choosing Attendee name from Insert field…](...)`.

## Admonitions

Use them sparingly — one per page at most.

```markdown
!!! tip "Save time"
    Duplicate last month's campaign instead of starting over.

!!! warning "This cannot be undone"
    Deleting a segment does not delete its contacts, but the segment is gone.
```

## Before you commit

Run the build locally and make sure it is clean:

```bash
pip install -r requirements.txt
mkdocs serve          # preview at http://127.0.0.1:8000
mkdocs build --strict # fails on broken links
```

`--strict` is what CI should eventually enforce. Do not add a page to `nav:` in
`mkdocs.yml` until the file exists, or the build breaks.

## Publishing

Pushing to `main` builds and publishes to <https://docs.goodbards.ai/>
automatically. It takes about a minute. If your change is not live after that,
check the **Actions** tab before assuming DNS.
