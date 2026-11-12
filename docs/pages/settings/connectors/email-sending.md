# Email sending

Choose how your marketing emails are sent: through GoodBards, or through your own
Amazon SES, Gmail or SendGrid account.

## What it's for

Before GoodBards can send an email campaign, it needs an **email server**: the
service that actually delivers your messages, from your own address. Without one,
sending fails. See [Emails](../../marketing/emails.md).

The **Email** tab of **Connections** offers four:

| Server | Choose it when… |
| --- | --- |
| **Goodbards** | You want GoodBards to deliver for you, from your own domain. Nothing to sign up for. |
| **Amazon-ses** | Your company already sends through its own Amazon SES account. |
| **Gmail** | You send small volumes from a Gmail or Google Workspace address. |
| **Sendgrid** | Your company already has a SendGrid account. |

## Before you start

- You must be an **administrator** or the **owner** of your GoodBards company
  account.
- Know the **sender name**, **sender address** and **reply-to address** your
  emails should use.
- For **Goodbards**, you need someone who can add **DNS records** to your domain
  (often your IT team or web agency).

## How to connect

1. Open your account menu (your picture, top right), then choose **Connections**.
2. Open the **Email** tab.
3. Choose the server's card, then **Connect**. Its settings open.
4. Fill in the fields for that server (below), plus the three sender fields:
   **Sender Name**, **Sender Address** and **Reply To Address**.
5. Save. The card shows a green tick once connected.

### Goodbards

- **Email Domain**: your domain only, for example `mycompany.com`, not an email
  address.
- Choose **Show DNS Records** and add every record listed to your domain's DNS:
    - a TXT record that proves you own the domain;
    - three CNAME records (DKIM) that sign your emails;
    - a TXT record for DMARC.

!!! warning "No DNS records, no reliable delivery"
    Until those records are in place, mail from your domain lands in spam or is
    refused. DNS changes can take a few hours to take effect.

### Amazon-ses

- **AWS Access Key ID** and **AWS Access Key Secret**: a key from your AWS account
  that is allowed to send with SES.
- **AWS Region**: the region where your SES is set up.
- **Email Domain**: the domain verified in your SES.

### Gmail

- **Gmail Address**: the address you send from.
- **App Password**: a Google *app password*, never your normal password. The
  settings panel links to Google's help on creating one.
- **SMTP Host** and **SMTP Port**: for Gmail, `smtp.gmail.com`.

### Sendgrid

- **API Key**: a SendGrid API key that can send mail.

## How to test the server

In the server's settings, choose **Test Config**, enter an **Email Address**, then
**Send Test Email**. Check that it arrives, and not in spam.

!!! tip "Test before every new setup"
    Send yourself a test after connecting and after any DNS change, before the
    first campaign goes out.

## What GoodBards does with it

| GoodBards… | Details |
| --- | --- |
| **Sends** | Your email campaigns and test emails, through the server you connected, from your sender address. |
| **Does not** | Read your mailbox. |

## Good to know

- **Use an address on your own domain.** With **Goodbards**, a sender address
  that is not on your domain (or one of its sub-domains) is replaced by your
  default sender.
- **Your plan sets a monthly sending allowance.** See
  [Usage & Billing](../tenant-usage.md).
- **Servers your plan does not include** show a crown.

## How to disconnect

1. On the **Email** tab, open the connected server's settings.
2. Choose **Disconnect**.

!!! warning "Sending stops"
    Emails can no longer be sent through that server until you connect one
    again, including campaigns already scheduled.

---

*Still stuck? [Contact support](../../contact.md).*
