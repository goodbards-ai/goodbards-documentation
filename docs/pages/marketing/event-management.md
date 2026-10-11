# Event Management

Run an event end to end: the registration page, the emails your guests receive,
the waitlist, check-in on the day, and the follow-up afterwards.

## What it's for

Events usually mean juggling a registration page, a spreadsheet of attendees, a
handful of emails and a clipboard at the door. Event Management keeps all of it on
one page, and because every registration becomes a contact, following up
afterwards does not mean re-typing a list.

## Before you start

- An **email design** for your brand, if you want the event emails to look like
  your other emails. Without one, they use the standard GoodBards design.
- A [form](forms.md), if the default registration form (name, email, company, job
  title) is not enough.

## How to set up an event

1. In the sidebar, choose **Marketing → Event Management**.
2. Choose **New Event** and fill in the name, type, date, time and venue.
3. Open the event. Its tabs follow the life of the event, left to right:
   **Overview**, **Definition**, **Landing page**, **Registration**,
   **Communications**, **Attendance**, **Analytics**, **Follow-up**.
4. Work through them in that order. Everything saves on its own; there is no
   Save button on the event page.

![The Event Management screen, showing events as cards with their status, date, time, venue and registration count](../../img/screenshots/event-management.png)

### Definition: what guests see

The **Definition** tab holds the cover image, the short and long descriptions, the
date and the address. These feed the landing page **and** every event email: the
event name, date and place in your emails always come from here. Change them here,
never inside an email.

### Landing page

The **Landing page** tab shows the page guests register on. It is built from the
Definition tab, so it is always up to date.

To change its layout, choose **Duplicate to customize**. You get your own copy in
the visual editor.

!!! warning "A customized page is a copy"
    Once you customize the landing page, later changes on the Definition tab are
    no longer copied into it. Update the page yourself, or go back to the default.

### Registration

- **Settings**: capacity, the registration window, **Require Approval**, and the
  **Waitlist**.
- **Registration form**: keep the default form, or choose **Create new** or
  **Duplicate existing** to use one of your own. **Edit form** opens it.
- **Contact registration**: which form fields fill the contact record (email,
  first and last name, phone, job title, tags, custom fields). See
  [Forms](forms.md).
- **Registration emails**: one email for each situation a guest can be in (see
  below).
- **Confirmation message**: the text shown on the page after registering.

The last four blocks are folded; click a title to open it.

### Registration emails

Each email is sent automatically when a guest reaches that situation. Only the
ones your event can produce are listed:

| Email | Sent when | Listed when |
| --- | --- | --- |
| **Confirmed** | The guest has a seat. Carries the check-in QR code and calendar links. | Always |
| **Request received** | The guest registered and waits for your approval. | **Require Approval** is on |
| **Approved** | You approved the request. | **Require Approval** is on |
| **Declined** | You declined the request. You can turn this one off. | **Require Approval** is on |
| **On the waitlist** | The event was full; the guest joined the waitlist. | **Waitlist** is on |
| **Spot opened** | A seat freed up and the guest moved off the waitlist. | **Waitlist** is on |

### Editing an email

Every event email (the registration emails above, and the invitation and
reminders under **Communications**) works the same way. The card shows the
email as guests receive it, inside your event design.

1. Click the preview, or **Edit**. The editor opens, with the **Subject** at the
   top and **Visual**, **Code** and **AI** on the side.
2. Change the text, then choose **Apply**. The card now says *Your own version of
   this email*.
3. To go back, choose **Reset to standard**.

In the **Visual** editor:

- **Purple dashed boxes** are parts only some guests see. The title says who,
  for example *Shown when the guest has a check-in QR code*. Edit the text
  inside; the box itself cannot be moved or deleted, so the email keeps working
  for every guest.
- **Purple chips**, such as **Attendee name** or **Event location**, are filled in
  for each guest when the email is sent. To add one, click into a text and pick
  it from **Insert field…** in the text toolbar. Do not type them by hand.

To send an email you built under **Emails** instead, choose **Use one of my
emails instead** under the card.

## How to send, and see what happened

1. On **Communications**, choose **Send Invitations** to email your audience, or
   **Send Reminder Now** for a reminder.
2. At the bottom of the tab, **Sent emails** lists every email the event has sent,
   with the time, the number of recipients and who sent it. Confirmations and
   other one-by-one emails are grouped per day.

    ![The Sent emails list: daily lines of confirmation emails sent automatically, and the invitation sent to 1,180 people by a team member, each with Recipients and Metrics](../../img/screenshots/event-sent-emails.png)

3. Choose **Recipients** on a line to see who received it, search them, or show the
   failed ones only. Choose **Metrics** for opens and clicks.
4. On **Attendance**, the **Latest email** column shows the last email each guest
   received. The eye icon opens the guest's **History with this event**: what was
   sent, delivered, opened and clicked.

    ![A guest's history with the event: registered, confirmation sent, delivered and opened, then the invitation sent, delivered, opened and a link clicked](../../img/screenshots/event-attendee-history.png)

5. On **Analytics**, **Email Performance** shows all the event's emails together
   or one type at a time, and **Export CSV** downloads the list.

## The waitlist

Turn on **Waitlist** under **Registration › Settings**. When the event is full,
new registrations join a queue. Choose how a freed seat is given:

- **Automatic**: the next person in line gets it and is emailed.
- **Manual**: you choose. On **Attendance**, use **↑ Promote** on a waiting guest.
  It only works when a seat is free.

## Checking people in

On the day, use **Scan attendee** to check people in. Each guest's confirmation and
reminder emails carry a QR code; scanning it records them as attended.

## The Actions menu

| Action | What it does |
| --- | --- |
| **Publish** / **Unpublish** | Puts the event page online, or takes it offline. |
| **Open public page** | Opens the event page as guests see it. |
| **Open** / **Close registration** | Starts or stops accepting registrations, without touching the event itself. |
| **Send invitations** | Emails the invitation to the event's audience. |
| **Scan attendee** / **Kiosk mode** | Checks guests in. See [Check-in and badges](../events/check-in.md). |
| **Export attendees** | Downloads the guest list as a spreadsheet. |
| **End event** | Ends it now; guests not checked in become absent. Ended events reopen with **Reopen** if you ended one too early. GoodBards also ends an event on its own when its end date passes. |
| **Cancel event** | Cancels it and emails every registered guest. Cannot be undone. |

To run an event again, duplicate its tactic on the campaign page: the event
comes with it. See [Duplicating a tactic](campaigns.md#duplicating-a-tactic).

The **Overview** tab also has quick actions: **Open Public Page**, **Copy
Registration Link** and **Preview Invitation Email**.

## Good to know

- **Publish before you share the link.** A draft event does not accept
  registrations.
- **Declined guests can stay unaware.** Turn off the **Declined** email and
  nobody you decline is emailed, even when you change a status by hand.
- **Cancel with ⊘, not with the status menu.** **Cancel registration** (the ⊘ icon
  on a row) emails the guest and offers the seat to the waitlist. Changing the
  status from the menu only corrects the list.
- **Follow up while it is fresh.** Attendees are contacts, so the **Follow-up** tab
  can email everyone who came, everyone who did not, or the people you invited who
  never registered.

---

*Still stuck? [Contact support](../contact.md).*
