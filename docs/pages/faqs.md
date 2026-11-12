# Frequently Asked Questions

## Account & access

### How do I reset my password?

Go to the [login page](https://live.goodbards.ai/login) and choose **Forgot
Password?**. You will receive an email with a reset link.

### How do I change my name, language or profile picture?

In **Personal Settings**, from your account menu (your picture, top right). See
[Personal Settings](settings/personal-settings.md).

### Can I turn on two-factor authentication?

Yes, under **Personal Settings → Password & Security**. Worth doing: a marketing
account can usually email your entire contact database.

### Why can I not see a section other people mention?

What appears in your sidebar depends on your plan and your permissions. Agentic
AI in particular is not included in every plan.

## Permissions

Most "the button is missing" or "the button is greyed out" questions come down
to one of two things: your **role** (which modules you can change), or the
**Access sensitive data** permission (whether you can handle personal details).
Hover a greyed-out button to see which one is missing. Both are set by an
administrator in **Tenant Settings → Security**. See
[Users, roles & permissions](settings/users-roles.md).

### Why is Add Contact greyed out for me?

Adding a contact needs the **Access sensitive data** permission, because the
contact form holds email, phone and address. The button says *Requires the
Access sensitive data permission*.

This permission is given **to a person, not to a role**, so being a Marketer,
an administrator or even the owner is not enough on its own. An administrator
gives it in **Tenant Settings → Security → Users**: the pencil in your
**Permissions** column, then tick **Access sensitive data** under
[Additional permissions](settings/users-roles.md#additional-permissions).

Only the **Sales** role includes it automatically.

### Why can I not create a segment?

Creating, editing and deleting segments needs **write access to the Audience
module**, which the **Marketer** and **Sales** roles include. You do not need
to be an administrator, and you do not need *Access sensitive data*: without
it you can still build segments, the contacts' emails and phones are simply
hidden inside them.

If **Add Segment** is missing, your role gives you read-only access to the
Audience. Ask an administrator to give you the Marketer role, or a custom role
with Audience write.

!!! note "Segments used to be administrator-only"
    Until November 2026 creating a segment required the Tenant Administrator
    role. That restriction is gone: any Audience writer can now manage
    segments.

### Why can I not import contacts or manage mailing lists?

**Bulk Add Contacts** (CSV import), creating a mailing list and adding or
removing its members need **both** the administrator role **and** *Access
sensitive data*. These change many contacts at once, so they stay with
administrators. A Marketer sees the button greyed out with the reason.

### Why are contacts' emails and phone numbers hidden?

You do not have *Access sensitive data*. Without it, personal details are
hidden everywhere: lists, contact pages, segments, exports and the assistant's
answers.

!!! warning "Deliberate, for PDPA"
    Under Singapore's PDPA and similar laws, give *Access sensitive data* only
    to people who work with contacts directly.

### I was given a permission but nothing changed

Permissions apply at your next login, or when you switch workspace. Log out and
back in.

### Why do I not receive the Daily Pulse email or chatbot lead alerts?

Each is sent only to people who have the matching additional permission:
*Recipient for daily report emails* and *Recipient for lead capture alert
emails*. If nobody in your company has it, nobody gets the email. See
[Additional permissions](settings/users-roles.md#additional-permissions).

### I can only see some contacts. Where are the others?

Your company has turned on **Restrict contacts to their owners**, and your role
(usually **Sales**) sees only the contacts and companies you own. Ask an
administrator to assign you as an owner, or to change your role. See
[Contact ownership](settings/users-roles.md#contact-ownership).

## Setting up

### What should I set up first?

Brand & Context, then your Brand Kit, then Connections, then contacts. See
[Sign Up & Onboarding](getting-started/signup-onboarding.md) for why that order.

### Why is there no data on my analytics pages?

Almost always a missing connector. Check
[Connections](settings/connections.md): pages such as Google Analytics and
Google Trends read from your own accounts and show nothing until those are
linked.

### Where is the LinkedIn Community connector?

It is now part of the **LinkedIn** connector. Connect LinkedIn once, and
**Mention…** appears in the post editor's **Insert** menu. See
[LinkedIn](settings/connectors/linkedin.md).

### I switched workspace in one tab, but my other tabs did not follow

That is deliberate. Each browser tab keeps its own workspace and its own
assistant conversation, so you can work on two clients side by side. A new tab
opens on the workspace you used last.

### Some pages take a while to load. Is that normal?

Yes. Screens that pull live data from Google can take several seconds. An empty
chart usually means it is still loading rather than that there is no data.

## Content & AI

### Does the AI know about my business?

It knows what you tell it in
[Brand & Context](settings/company-settings.md): what your company does, how it
sounds, who it competes with. Filling that in properly is the single biggest
improvement you can make to AI output.

### Can I control what the AI can see?

Yes. Each field in Brand & Context has a **Visible to AI** / **Hide From AI**
toggle, so you can keep commercially sensitive details out of generated content.

### Why could a web page not be read?

Some sites tell automated tools not to read their pages, through a file called
robots.txt. GoodBards respects it: such pages are skipped with the message *The
site owner does not allow automated access to this page*. Copy the text you
need and paste it in instead.

### Which AI model is used?

Set per generation type (text, image, video and audio) in
[AI Settings](settings/ai-settings.md). The defaults work well; change them only
if you have a specific reason.

### Does generating content cost anything?

It consumes credits from your monthly allowance. Video costs more than images,
which cost more than text. Track it in
[Usage & Billing](settings/tenant-usage.md).

## Campaigns & publishing

### What is the difference between a tactic and a campaign?

A **tactic** is one piece of marketing on one channel, such as a single post or one email.
A **campaign** groups several tactics towards one goal over a period of time. If
you just want to publish one post, you want a tactic. See
[Launch a Tactic](marketing/launch-tactic.md).

### Why is my ad campaign not spending anything?

New campaigns start **paused**, and need at least one enabled ad. See
[Digital Ads](marketing/digital-ads.md).

### Can I recall an email after sending it?

No. Check your recipient list and send yourself a test first. See
[Emails](marketing/emails.md).

## Audience & data

### What happens if someone unsubscribes?

They move to the unsubscribed group and stop receiving marketing email, whether
you send to chosen contacts, a segment or a mailing list. Do not work around
this by re-importing them: under Singapore's PDPA and equivalent rules
elsewhere, opt-outs must be respected. See
[Unsubscribed contacts](audience/contacts.md#unsubscribed-contacts).

### How do I find contacts who stopped engaging, and keep them out of a send?

There is no automatic "unengaged" status. Each contact has a decay score that
fades to zero over the period your administrator sets (4, 8 or 12 weeks).
Create a segment on *Decay Score less than 1* to find them, or on the opens and
clicks of the last N days for a rule of your own, and send to a segment that
leaves them out. See
[Unengaged contacts](audience/contacts.md#unengaged-contacts).

### What is the difference between a segment and a mailing list?

A **segment** is a saved rule, re-evaluated each time you use it, so it stays
current. A **mailing list** is a fixed set of contacts. See
[Contacts](audience/contacts.md).

### Can I keep separate workspaces for different clients?

Yes, if your plan includes sub-workspaces. Each has its own contacts, campaigns
and credit allowance. See [Sub-Workspaces](settings/users-access.md).

---

Not answered here? [Contact support](contact.md).
