# Scheduler

Run recurring work on a schedule: an AI agent's report every Monday, a social
report every month, a web page checked every morning.

## What it's for

Some work is the same every week: summarise last week's results, check a
competitor's page, collect the social figures for a client. The Scheduler does
it for you at the time you choose, and sends you the result by email or saves it
in your Content Repository.

## Before you start

- **Your plan.** The Scheduler is included in the **Pro** and **Full** plans.
- **What the task needs.** An agent for an agent run, a connected social
  account for a social report, a connected Google Drive for a Drive sync. See
  [Connections](../settings/connections.md).

## How to schedule a task

1. In the sidebar, choose **Tool Box → Scheduler**, then **New Task**.
2. Give the task a **Name** and, if you like, a **Description**, then pick the
   **Task type**:

    ![The New scheduled task dialog: Name, Description, and the task types Agent run, Social report, Web scrape and Drive sync, in three steps Name & type, Details and Schedule](../../img/screenshots/scheduler-new-task.png){ width="65%" }

    | Task type | What it does |
    | --- | --- |
    | **Agent run** | Asks one of your AI agents, chat or workflow, a question, for example *"Summarise last week's campaign results"*. |
    | **Social report** | Builds the period report of one of your social accounts. |
    | **Web scrape** | Scrapes a page, crawls a website or reads a feed into your Content Repository, for example a competitor's pricing page. |
    | **Drive sync** | Keeps a Google Drive folder in sync with your Content Repository. |
    | **Email a report** | Emails the results of chosen campaigns and automation flows, with a CSV attached. See [Email a report](#email-a-report). |

3. Choose **Next**, then fill in the **Details**: which agent and what to ask,
   which social account, which page. For an agent run, choose where the answer
   goes: an **email** to you or your colleagues, a document in your **Content
   Repository**, or both.
4. Choose **Next**, then set the **Schedule**: how often and at what time.
5. Choose **Create Task**. The task appears in the list with its schedule.

From the task's menu, **Run now** starts it straight away, **History** shows
its past runs, and **Edit** or **Delete** change or remove it.

!!! warning "Deleting a task also deletes its history"
    The task and its run history are removed, and this cannot be undone. To
    pause a task instead, turn off **Enabled**.

## Email a report

A weekly results email, for you, your team or a client, with every figure in an
attached CSV: for example every Monday at 08:00.

1. Create a task of type **Email a report**.
2. Under **Details**, tick the **Campaigns** and **Automation flows** to report
   on (up to 30), and choose **Emails to include**:
    - **Sent in the last 7 days**: the emails sent in the week before the run,
      with what their recipients did since;
    - **Every email, figures to date**: every email of the campaigns and flows.
3. Under **Send the report to**, pick members of your workspace, and add up to
   5 addresses outside it (a client's manager, for example).
4. Set the **Schedule**, for example **Weekly**, **Monday**, **08:00**, your
   timezone.

The email shows a short table of the emails; the attached CSV has one row per
email: the campaign or flow, the tactic or step, the split lane, the email, when
it was first sent, then sent, delivered, opened and clicked by real people (with
rates), opened and clicked by machines, unsubscribed, spam complaints and
bounced. An [A/B test](../marketing/ab-testing.md) gives one row per version.

!!! info "Totals only"
    The report never lists contacts: it can be forwarded without sharing anyone's
    personal data. To see who opened or clicked, use the email's or the flow's
    **Recipients**, or the API.

## Good to know

!!! info "A scheduled agent does not act on its own"
    When it runs unattended, it will not send a campaign email or publish
    content; it can prepare them for you.

- **A task runs as the person who created it**, with that person's access. An
  administrator can choose someone else under **Run as**.
- **If the delivery fails, the run still counts.** For example, the agent answers
  but the email cannot be sent: the history shows the run in amber with the
  reason.

---

*Still stuck? [Contact support](../contact.md).*
