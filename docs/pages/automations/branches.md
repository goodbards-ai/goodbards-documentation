# Branches and conditions

Send different contacts down different lanes: those who clicked and those who
did not, retail and education, hot and cold leads.

## What it's for

A branch checks something about the contact and splits the flow into lanes,
one per answer. The lanes sit side by side on the canvas and **join again
below**, so the steps after the branch run for everyone, unless a lane ends with
**Exit flow**.

!!! abstract "In short"
    | You want | Use |
    | --- | --- |
    | Two lanes: yes or no | **Yes / No branch** |
    | Three or more lanes, checked in order | **Routing** |
    | The AI to judge, for example hot / warm / cold | **AI decides** |
    | Some contacts to stop here | A lane that ends with **Exit flow** |
    | Some contacts to skip a step | An empty lane |

## Yes / No branch

One condition, two lanes: contacts who match it, and everyone else.

![The Welcome series flow: Wait for a click, then a Yes / No branch with the lanes Clicked (add a tag) and Did not click (a reminder email) joining again before the last tag](../../img/screenshots/automations/tutorial-welcome-series-canvas.png)

1. Add **Yes / No branch** where the flow should split.
2. In the side panel, name the first lane under **Lane label** and pick its
   **Condition**.
3. Name the **Last lane** (everyone else).
4. Add steps inside each lane with its **+**.

![The Yes / No branch panel: lane label Clicked, condition Opened or clicked an email, on the email sent by Tutorial · Getting started, counts as engaged when Clicked](../../img/screenshots/automations/panel-yes-no-branch.png){ width="30%" }

*Sample: [Tutorial 2 · Welcome series](samples.md#2-welcome-series).*

## Routing

Several rules, **checked from left to right: the first that holds opens its
lane**. Contacts who match none take the last lane.

![The Route by interest flow: a Routing step with the lanes Retail, Education, Key accounts and Everyone else, joining again into Set field and Remove tag](../../img/screenshots/automations/tutorial-route-by-interest-canvas.png)

Choose **Add Rule** in the panel for each lane, and reorder rules with the ↑ ↓
arrows: order matters when a contact could match two rules.

![Rule 1 of a routing: lane Retail, condition Field value, field industry, equal to Retail](../../img/screenshots/automations/panel-routing-rule-field.png){ width="30%" }
![Rule 3 of a routing: lane Key accounts, condition Has tag, tags vip and key-account, match any of them](../../img/screenshots/automations/panel-routing-rule-tags.png){ width="30%" }

*Sample: [Tutorial 3 · Route by interest](samples.md#3-route-by-interest).*

## AI decides

The AI answers one question about the contact and picks a lane. See
[AI and human steps](ai-steps.md#ai-decides).

## The conditions

The same conditions work in branches, routing, [goals and stop
rules](settings.md):

| Condition | True when |
| --- | --- |
| **Has tag** | The contact has the tag. Several tags: **any** or **all** of them. |
| **Field value** | A contact field is equal to, not equal to, contains, is one of, is empty, is not empty, greater or less than a value. You pick the field from the same list as in segments: contact fields (city, country, Customer Type, preferred language, timezone, created on, birth date…) and your custom fields. Pick-list fields offer their values. Dates compare as `YYYY-MM-DD`, for example created on greater than `2026-01-01`. |
| **Score** | Under **Field value**, group **Scores**: **Engagement Score** or **Decay Score** (the same, faded with time: "engaged lately"), for example Decay Score greater than `50`. They are the two scores of the contact page. |
| **In segment** | The contact is a member of the segment right now. |
| **Opened or clicked an email** | The contact opened (or clicked) an email sent earlier in this flow. |
| **Outcome of a task** | A **Task for the owner** earlier in the flow was done, dismissed or timed out. |
| **What an earlier step wrote** | A value an agent, a task or an AI decision stored for this contact. |
| **An answer in the form** | Flows started by a form: an answer in the submission that started the flow, for example `form.rating` less than `3`. Pick it under **What an earlier step wrote**. |

!!! note "Owner, mailing list, consent, tags"
    These are not in the field list. Use **Has tag**, or build a segment
    (owner, mailing list, "can be messaged on") and use **In segment**.

!!! note "Customer Type"
    **Customer Type** is the B2B / B2C choice of the contact page. It does not
    say whether the contact bought. For that, use a tag (for example
    `status: customer`) or a pick-list custom field.

!!! tip "Survey answers"
    Use **An answer in the form** rather than a custom field to branch on a
    survey score. A form fills a custom field only when it is empty, so a
    contact's second survey would still show the first score.

![A branch on the outcome of a task: lane Approved, condition Outcome of a task, task Review the email, counts when Done](../../img/screenshots/automations/panel-branch-task-outcome.png){ width="30%" }

## Exit lanes and empty lanes

- A lane that ends with **Exit flow** takes its contacts out: the lanes that
  join again below are the others.

    ![The Win back flow: the Opened lane adds a tag and continues to What's new; the No reaction lane adds dormant and exits](../../img/screenshots/automations/tutorial-win-back-canvas.png)

- An **empty lane** means "skip": its contacts go straight to the step after the
  branch. *Sample: [Tutorial 5](samples.md#5-monthly-check-in).*

## Good to know

- **Checked once, when the contact reaches the branch.** A branch does not
  wait: put a **Wait for open / click** before a branch on an email.
- **Lanes can hold branches**, but keep flows readable: past three levels,
  split into two flows connected by a tag.
- **Stop anywhere** is not a branch: for "stop as soon as they buy", use a
  stop rule in [Flow settings](settings.md).

---

*Still stuck? [Contact support](../contact.md).*
