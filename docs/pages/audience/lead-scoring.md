# Lead scoring

A score per contact, from what they actually did: opened, clicked, registered,
came to your event. Use it to see who is ready for a conversation.

## What it's for

A list of 3,000 contacts does not tell you who to call first. The score does.
Every engagement adds points, the strongest signals add the most, and points
fade over time, so the people at the top are the ones engaging **now**.

## How to see a contact's score

In the sidebar, choose **Audience → Contacts**, then open a contact. Next to
their name:

- **Engagement Score**: all the points they have earned.
- **Decay Score**: the same points, faded with time. Recent activity counts
  fully, older activity less.

![A contact's name with an Engagement Score of 10 and a Decay Score of 10, and the status Subscribed](../../img/screenshots/contact-scores.png)

The contact's **Engagement Distribution** shows where the points come from.

## How points are earned

Points follow one ladder: about **100 points** is a guest who registered for an
event and came. Everything else is measured against that.

| Signal | Effect on the score |
| --- | --- |
| Opening an email | A few points, **once per email**. Opening it again adds nothing. |
| Clicking a link in an email | More than an open, once per link per email. |
| Filling in a form | More again: the contact raised their hand. |
| Registering for an event, and attending | The strongest signals. |
| Missing an event they registered for | Points taken off. |
| Unsubscribing, or asking not to be contacted | A large number of points taken off. |
| A hard bounce (invalid email) | The score drops to zero. |

!!! info "Only what the contact does counts"
    Sending or delivering an email gives no points: the contact did nothing yet.
    Scores update once a day, so today's activity shows tomorrow.

## Good to know

!!! tip "Use the decay score to prioritise"
    Two contacts with the same engagement score are not equal if one engaged
    last week and the other last year.

- **You choose how fast points fade.** An administrator sets the **Engagement
  Decay Velocity** in **Tenant Settings → Preferences**: 4 weeks (fast), 8
  weeks (normal), 12 weeks (slow), or no decay. Points fade evenly to zero over
  that period.
- **Four tiers.** The Contacts home groups contacts by decay score: **High**
  (100 and more), **Medium** (40 to 99), **Low** (1 to 39) and **Inactive** (0,
  or never engaged). A segment on the score finds the quiet ones. See
  [Unengaged contacts](contacts.md#unengaged-contacts).
- **Companies are scored too**, from the engagement of their contacts. See
  [Companies](companies.md).

---

*Still stuck? [Contact support](../contact.md).*
