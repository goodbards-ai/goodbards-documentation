# Pipedrive

Bring the people and organisations from your Pipedrive CRM into your GoodBards
contacts.

## What it's for

If your sales team works in Pipedrive, the **Pipedrive** connector saves you
re-typing contacts. Once connected, the **Import Pipedrive Contacts** page brings
your Pipedrive people, then your organisations, into
[Contacts](../../audience/contacts.md).

## Before you start

- You must be an **administrator** or the **owner** of your GoodBards company
  account.
- You need two things from Pipedrive:
    - your **company name** as it appears in your Pipedrive address — the
      `yourcompany` in `yourcompany.pipedrive.com`;
    - your personal **API token**, from your Pipedrive personal preferences.
- Decide which **privacy statement** and **status** imported contacts should get.
  See [Adding contacts](../../audience/adding-contacts.md).

## How to connect

1. Open your account menu (your picture, top right), then choose **Connections**.
2. On the **CRM** tab, find **Pipedrive** and choose **Connect**.
3. Fill in:
    - **Tenant Name**: your Pipedrive company name.
    - **Access Token**: your Pipedrive API token.
4. Choose **Save Settings**. The card shows your Pipedrive user name.

## How to import your contacts

In **Audience → Contacts → Import Jobs**, choose **Bulk Add Contacts → From
Pipedrive**. On **Import Pipedrive Contacts**, fill in:

| Field | What it does |
| --- | --- |
| **Title** | A name for this import. |
| **Choose Conflict Action** | **Ignore** keeps existing contacts as they are; **Overwrite** updates them from Pipedrive. |
| **Default Status** | The status imported contacts get. Only *subscribed* contacts receive emails. |
| **Tags** | Tags added to every imported contact. |
| **Privacy Statement** | The statement the contacts agreed to. Your company default is filled in. |
| **Notes** | A note added to each contact. |

Choose **Upload** to start. Every imported contact gets the referral source
**Pipedrive Contacts Import**. The import runs in the background.

## What GoodBards does with it

| GoodBards… | Details |
| --- | --- |
| **Reads** | Your Pipedrive people and organisations, and your own Pipedrive user. |
| **Does not** | Write anything back to Pipedrive, or read deals. |

## Good to know

- **It is a one-off import, not a live sync.** Run it again to pick up new people.
- **Import only people who agreed to hear from you.** Choose the status with care.

## How to disconnect

1. On the Pipedrive card, choose **Disconnect**.
2. Confirm.

Contacts already imported stay in GoodBards.

---

*Still stuck? [Contact support](../../contact.md).*
