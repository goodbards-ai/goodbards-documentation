# Google BigQuery

Let GoodBards read your own BigQuery data, so your AI agents can answer
questions from your warehouse.

## What it's for

If your company keeps its data in Google BigQuery (website events, sales,
subscriptions), the **Google BigQuery** connector lets GoodBards read it. Your
data stays in your Google project: GoodBards runs read-only queries there and
copies nothing.

!!! note "Set up with your data team"
    Connecting needs a key file that only someone with access to your Google
    Cloud project can create. The steps below tell them exactly what to do.
    Once you have the file, the GoodBards side takes two minutes.

## Before you start

- You must be an **administrator** or the **owner** of your GoodBards company
  account.
- Ask your data team for a **service-account key file** (a `.json` file). Send
  them this checklist:
    1. In the Google Cloud project that holds the data, create a service
       account named for GoodBards.
    2. Give it **BigQuery Data Viewer** on each dataset GoodBards may read, and
       **BigQuery Job User** on the project.
    3. Create a **JSON key** for that service account and send you the file.
- Queries are billed to that Google Cloud project, at BigQuery's usual rates.
  A cap limits what one query may scan (1 GB unless you change it).

## How to connect

1. Open your account menu (your picture, top right), then choose **Connections**.
2. On the **Web Analytics** tab, find **Google BigQuery** and choose **Connect**.
3. Choose **Choose file** and pick the key file, or paste its content in the
   box below. GoodBards shows the account it found in the file.
4. **GCP project** is filled in from the file. Change it only if your data team
   told you to.
5. Choose **Save & connect**. GoodBards checks the key with Google and lists
   the datasets it can see before saving. If Google refuses, nothing is saved
   and the message tells you why.

The card then shows the service account and the project. **Manage
configuration** opens the same form; **Test connection** lists the datasets
again at any time.

## What GoodBards does with it

| GoodBards… | Details |
| --- | --- |
| **Reads** | Only the datasets your data team granted. Queries are read-only and run in your project. |
| **Stores** | The key file, encrypted. It is never shown again, not even to administrators. |
| **Does not** | Change anything in BigQuery, copy your tables, or read datasets the account was not granted. |

## Good to know

- **Under Advanced**, you can raise or lower the per-query cost cap. Leave it
  unless your data team asks for more.
- To rotate the key, open **Manage configuration**, choose **Replace key**,
  pick the new file and save. The old key stops being used immediately.
- Some companies block the creation of service-account keys by policy. If your
  data team cannot create one, contact support before going further.

## How to disconnect

1. On the Google BigQuery card, choose **Manage configuration**.
2. Choose **Disconnect**. The stored key is deleted.

---

*Still stuck? [Contact support](../../contact.md).*
