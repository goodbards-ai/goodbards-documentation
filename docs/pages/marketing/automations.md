# Automations

Send each contact a sequence of emails, waits and follow-ups that runs on its
own once you switch it on.

## What it's for

A flow is a path one contact walks through: a welcome email, a wait of three
days, a second email only for those who opened the first, a tag at the end.
You design it once; GoodBards then runs it separately for every contact who
enters, at their own pace.

Use it for welcome sequences after a sign-up form, nurture series for new leads,
re-engagement of quiet contacts, or a monthly touchpoint for a segment.

## Before you start

- **Your plan.** Automations is part of the Pro and Team plans. If
  **Automations** shows a crown in the sidebar, your plan does not include it;
  speak to your account contact.
- **Your access.** Flows sit with emails, so you need the **Emails and forms**
  access (write, to build and activate flows). See
  [Users, roles & permissions](../settings/users-roles.md).
- **An email server.** Flows send through the server connected under
  **Connections**. See [Email sending](../settings/connectors/email-sending.md).
- **The emails themselves.** Each email in a flow is one of your
  [Emails](emails.md). Create them first, or add the flow's steps and pick the
  emails afterwards.
- **Subscribed contacts.** Only contacts whose status is **Subscribed** stay in
  a flow (see [Good to know](#good-to-know)).

## How to build a flow

1. In the sidebar, choose **Marketing → Automations**, then **New flow**.
2. Give it a **Name** and, if you like, a **Description**, then choose
   **Create**. The designer opens.

    <!-- screenshot: the flow designer with a trigger card, a Send email, a Wait and a Yes / No branch, palette on the left and side panel on the right -->

3. Select the **Trigger** card at the top and pick what enrols a contact under
   **Starts when** (see [Triggers](#triggers)). Fill in the form, tag or segment
   it asks for.
4. Add steps. From the palette on the left, click a step to add it after the
   selected card, or drag it onto a **+** between two cards. You can also use
   **Edit → Add step**.
5. Select each card and fill in its settings in the side panel on the right:
   the email to send, how long to wait, the tag to add.
6. Open **File → Flow settings** to choose the re-entry rule, a goal and any
   **Stop early when…** rules (see [Flow settings](#flow-settings)).
7. Choose **Save**. An unfinished flow can be saved; the cards still missing
   something are highlighted.
8. When every card is complete, choose **Activate**. New contacts enrol from
   that moment.

!!! tip "Test it on a few people first"
    Once the flow is active, open its **Contacts** tab and choose **Enroll
    contacts** to run it on yourself or a couple of colleagues before the real
    audience arrives. (On a **Manual** flow, the same button sits on the
    **Trigger** card in the designer.)

### Other ways to start

- **Duplicate** an existing flow from its menu in the list.
- **AI assistant**: in the designer, switch the view to **AI assistant**, paste
  a brief or describe the flow in your own words. It asks up to five questions,
  then proposes a flow. Choose **Apply to the canvas**, review it, then
  **Save**. It also lists the emails you still need to create.
- **Import JSON…**: load a flow someone exported with **Export as JSON**, for
  example from another workspace.

## Triggers

The trigger decides who enters the flow. Only events after you activate the
flow count: earlier form submissions, tags or contacts are never picked up.

| Trigger | Who enters |
| --- | --- |
| **Manual** | Only the contacts you enrol yourself, by hand, from a segment or from a mailing list. |
| **Form submitted** | The contact of every new submission of the chosen form, within a minute. |
| **Contact created** | Every contact added after activation, within a minute. |
| **Tag added** | A contact who gets the chosen tag, within a minute, whoever adds it. |
| **Segment (daily)** | Every day at 03:00 UTC, members of the segment who are not in the flow yet. |
| **On a schedule** | Members of the segment, each time the schedule runs: every day, week or month at a time and timezone you choose. |

Whatever the trigger, you can also enrol contacts yourself while the flow is
active: on the flow's **Contacts** tab, choose **Enroll contacts** and pick
**Contacts**, a **Segment** or a **Mailing list** (up to 2,000 at a time).

## Steps

| Step | What it does |
| --- | --- |
| **Send email** | Sends one of your emails, as it is at send time, with the contact's details, tracking and the unsubscribe link. |
| **Wait** | Pauses for a number of minutes, hours or days (up to 365 days). |
| **Wait for open / click** | Pauses until the contact opens or clicks an earlier email of the flow, or a time limit passes. |
| **Add tag** | Puts a tag on the contact. |
| **Remove tag** | Takes a tag off the contact. |
| **Set field** | Writes a value into one of the contact's custom fields. |
| **Ask an agent** | Asks one of your AI agents about the contact. Its answer, free text or a drafted email, is kept for the next steps. |
| **Task for the owner** | Puts a task in **Actions** for the contact's owner or a named colleague. The flow waits until it is done, dismissed or past its deadline. |
| **Send drafted email** | Sends the email an **Ask an agent** step drafted, inside one of your email designs. |

The palette's **Structure** group splits contacts into lanes:

| Step | What it does |
| --- | --- |
| **Yes / No branch** | Two lanes: contacts who match a condition, and everyone else. |
| **Routing** | Several lanes, one per rule, checked in order, plus a lane for everyone else. |
| **AI decides** | The AI answers one question about the contact (for example *Is this lead hot, warm or cold?*) and sends them down the matching lane. When it is not sure enough, they take the last lane. |
| **Exit flow** | The contact leaves the flow here. |

Conditions in branches, routes, goals and exit rules can check a tag, a field
value, membership of a segment, whether the contact opened or clicked an
earlier email, the outcome of a task, or what an earlier step wrote.

Under **Decoration**, **Add note** puts a sticky note on the canvas for your
colleagues. Contacts never see it.

## Flow settings

In the designer, choose **File → Flow settings**.

| Setting | What it decides |
| --- | --- |
| **Send emails with** | Which email server sends, when you have more than one connected. |
| **Re-entry** | **Once per contact** (the default); **Every time the trigger fires again (after finishing)**; or **After a cooldown**, with the number of days before the same contact can enter again. |
| **AI budget per month** | The most credits this flow may spend on **Ask an agent** and **AI decides** steps each calendar month. Empty means no cap. |
| **Goal** | What the flow is for, for example *Booked a demo*. A contact who meets it leaves the flow and counts as a conversion in the report. |
| **Stop early when…** | Rules that take a contact out as soon as something becomes true, such as a purchase. A rule can also move them into another flow. |

## Running a flow

A flow's status shows in the list:

| Status | What it means |
| --- | --- |
| **Draft** | Being built. Nobody enters. |
| **Active** | Running. New contacts enrol as the trigger fires. |
| **Paused** | Contacts hold where they are, and nobody new enrols until you choose **Resume**. |
| **Archived** | Finished for good. Everyone still in it leaves. It can be viewed but not edited. |

**Changing an active flow.** Edits go into a draft; the flow keeps running as
it was. Choose **Activate changes** to publish them. Contacts already in the
flow finish on the version they started; new contacts get the new one.

## Following the results

From the list, choose a flow's menu, then **Contacts & report**.

<!-- screenshot: a flow's page on the Report tab, the canvas with reached counts and opens/clicks on each email card -->

- **Contacts** lists everyone who entered, with their status, the step they are
  on and why they left. Filter by **In flow**, **Completed**, **Exited**,
  **Skipped** or **Failed**. **Path** shows the cards a contact went through,
  with the time of each. **Wake now** ends a contact's current wait early;
  **Remove** takes them out of the flow.
- **Report** draws the flow with how many contacts reached each card, the
  sent, opened and clicked figures of each email, and how lanes split. With a
  goal, it also shows **Goal reached** and the **Conversion** rate.

A contact's own page also lists the flows they have been in, under
**Automation flows**.

## Using a flow in a campaign

In a campaign, add a **Marketing Automation** tactic. In the tactic, choose
**Create the flow**, or pick one you already have and choose **Link**. The
tactic then shows how many contacts are **In the flow**, **Completed** and
**Exited**, and the flow's emails reach the campaign report.

The tactic follows the flow: activating the flow starts the tactic, archiving
it completes the tactic. See [Campaigns](campaigns.md).

## Good to know

- **Only subscribed contacts stay in a flow.** A contact who is not
  **Subscribed** (regular, unsubscribed, bounced, do not contact) leaves every
  flow within a minute, wherever they are, even if the flow sends no email. An
  unsubscribe from any email therefore ends their flows.
- **One flow at a time.** A contact already in a flow is skipped by any other
  flow's trigger. The skip is listed on that flow's **Contacts** tab under
  **Skipped**, so you can see who missed out.
- **Nothing is backfilled.** Activating a form-triggered flow does not enrol
  people who filled in the form last week. Enrol them yourself if you need to.
- **Goals and exit rules are checked before each step,** not during a wait. A
  contact on a three-day wait who books a demo on day one leaves when the wait
  ends, before the next email goes out.
- **Emails are sent as they are at send time.** Editing an email changes what
  the next contacts receive, even mid-flow.
- **A failing step is retried twice.** After the third failure, for example
  with no email server connected, the contact is marked **Failed** and leaves.
  The same happens to **Ask an agent** and **AI decides** steps once the flow's
  monthly AI budget is spent.
- **Review AI-drafted emails.** Put a **Task for the owner** before a **Send
  drafted email** step so a colleague approves or edits the draft in
  **Actions** before it goes out.
- **Delete only what never ran.** You can delete a draft, or an archived flow
  that never had a contact. Otherwise, archive it: archiving cannot be undone.
- **A flow has at most 50 steps.**

---

*Still stuck? [Contact support](../contact.md).*
