# WhatsApp

Send your campaign messages on WhatsApp, from your own WhatsApp Business number.

## What it's for

With the **WhatsApp** connector, GoodBards sends WhatsApp messages
to the contacts who agreed to receive them, from **your** number and under
**your** business name. Everything goes through your own Meta account: Meta bills
you directly for the messages, and GoodBards never pays or sees your Meta bill.

!!! note "In development"
    Today you can connect your WhatsApp number and check its status. Message
    templates and sending to your contacts arrive next. Meta's screens are made
    for developers: if you would rather not do this alone, contact support and we
    set it up with you on a short call.

## Before you start

- WhatsApp is included in the **Pro** and **Full** plans.
- You must be an **administrator** or the **owner** of your GoodBards company
  account.
- You need a Facebook account that is an administrator of your company's
  **Meta business portfolio** (business.facebook.com). Ideally the portfolio is
  already verified by Meta.
- Allow 20 to 30 minutes. You do this once.

## The GoodBards form, field by field

At the end, GoodBards asks for four details. Here is what each one is, in plain
words, and where it comes from. The steps below collect them one by one.

![The Connect WhatsApp form in GoodBards](../../../img/screenshots/whatsapp/16-goodbards-form.png)

| Field in GoodBards | What it is | Where Meta shows it | Looks like |
| --- | --- | --- | --- |
| **WhatsApp Business Account ID** | Your WhatsApp account at Meta, which holds your number(s) and message templates. Meta now calls it **Messaging account ID**. | Your app's WhatsApp setup page (step 2), or Business settings → **Messaging accounts** → your account → **ID** | 15–16 digits, e.g. `102290129340398` |
| **Phone number ID** | Meta's internal number for your sending phone line. **Not** the phone number itself. | Your app's WhatsApp setup page, next to the number (step 2) | 15–16 digits, e.g. `106540352242922` |
| **Permanent access token** | The key that lets GoodBards send in your name. Shown only once. | Business settings → **System users** → **Generate token** (step 4) | A long text starting with `EAA` |
| **App secret** | Proves that messages and updates really come from your Meta app. | Your app → **App settings → Basic → App secret → Show** (step 3) | 32 letters and digits |

!!! tip "Keep a note open"
    Paste each detail in a private note as you go (your password manager is
    ideal), then copy them into GoodBards at the end.

## How to set up WhatsApp in Meta

### 1. Create a Meta app

The app is your company's "mailbox" at Meta for sending WhatsApp messages.

1. Go to **developers.facebook.com**, log in, and choose **My Apps → Create App**.
2. Give the app a name, for example *Your brand Messaging*. Meta refuses names
   that contain "WhatsApp".

    ![The Create an app screen: App name and App contact email](../../../img/screenshots/whatsapp/01-app-name.png)

3. Choose **Next**, then tick **Connect with customers through WhatsApp**.

    ![The use cases list with "Connect with customers through WhatsApp" ticked](../../../img/screenshots/whatsapp/02-use-case.png)

4. Choose **Next** and pick your company's business portfolio.

    ![Choosing the business portfolio to connect to the app](../../../img/screenshots/whatsapp/03-business-portfolio.png)

5. Choose **Next** twice. The **Requirements** step lists *Business verification*
   and *App Review*: App Review is only for apps that access other businesses'
   accounts, so it does not stop you from sending from your own number.
6. Check the summary and choose **Create app**. This accepts Meta's Platform
   Terms for your business.

    ![The overview before creating the app](../../../img/screenshots/whatsapp/04-overview.png)

### 2. Copy the Phone number ID and the WhatsApp Business Account ID

1. On the app's dashboard, choose **Customize the Connect with customers through
   WhatsApp use case**.

    ![The app dashboard with its setup checklist](../../../img/screenshots/whatsapp/05-dashboard.png)

2. Meta shows a guided setup. Choose **Step 1. Try it out**.

    ![Meta's guided WhatsApp setup](../../../img/screenshots/whatsapp/06-guided-setup.png)

3. Meta gives you a free **test number**. Next to it:
    - **Phone Number ID** → paste it in GoodBards' **Phone number ID**.
    - **Messaging account ID** → paste it in GoodBards' **WhatsApp Business Account ID**.

    ![The test number with its Phone Number ID and Messaging account ID](../../../img/screenshots/whatsapp/07-test-number-ids.png)

The test number is enough to try GoodBards. To send from your real number, follow
**Step 2. Production setup** on the same page: add your number, then a payment
method. Your real number then has its own Phone number ID, shown in the same place.

### 3. Copy the app secret

1. In the app, open **App settings → Basic** (left menu, near the bottom).
2. Next to **App secret**, choose **Show**. Meta asks for your Facebook password.
3. Copy the secret → GoodBards' **App secret**.

![App settings, Basic: the App secret field with its Show button](../../../img/screenshots/whatsapp/08-app-secret.png)

### 4. Create the permanent access token

GoodBards needs a key that does not expire. Meta gives such keys to a **system
user**: a robot account of your company that can only do what you allow. You
create it, give it access to your app **and** to your WhatsApp account, then
generate its key.

**a. Create the system user**

1. Go to **business.facebook.com → Settings → Users → System users** and choose
   **Add**. The first time, Meta asks you to accept its non-discrimination policy.

    ![Meta's non-discrimination policy, shown before the first system user](../../../img/screenshots/whatsapp/09-system-user-policy.png)

2. Name it, for example *GoodBards Sender*, keep the role **Employee**, and choose
   **Create system user**.

    ![Creating the system user](../../../img/screenshots/whatsapp/10-create-system-user.png)

3. With the system user selected, choose **Assign assets → Apps**, tick your new
   app, turn on **Develop app**, and choose **Assign assets**.

**b. Give it access to your WhatsApp account** (the step people miss)

1. Still in Settings, open **Accounts → Messaging accounts** and select your
   WhatsApp account.
2. Choose **Assign people**, tick your system user, turn on **Everything** (full
   access), and choose **Assign**.

    ![Assign people: the system user with full access to the messaging account](../../../img/screenshots/whatsapp/17-messaging-account-assign.png)

3. On the account's **People** tab, check that your system user is listed under
   **People with full access**.

    ![The messaging account's People tab, with the system user under full access](../../../img/screenshots/whatsapp/18-messaging-account-people.png)

!!! warning "Use Messaging accounts, not WhatsApp accounts"
    Meta also lists your account under **Assign assets → WhatsApp accounts** on
    the system user page. Giving access there is not enough: GoodBards then shows
    "Meta cannot find this WhatsApp Business Account". Always check the **People**
    tab of the messaging account.

**c. Generate the key**

1. Back in **System users**, select your system user and choose **Generate token**.
2. Pick your app.

    ![Generate token: choosing the app](../../../img/screenshots/whatsapp/12-token-app.png)

3. Set the expiry to **Never**. With 60 days, your WhatsApp sending would stop
   until you create a new token.

    ![Token expiry set to Never](../../../img/screenshots/whatsapp/13-token-never.png)

4. Tick **whatsapp_business_management** and **whatsapp_business_messaging**, then
   choose **Generate token**.

    ![The two WhatsApp permissions ticked](../../../img/screenshots/whatsapp/14-token-permissions.png)

5. **Copy the token right away** → GoodBards' **Permanent access token**. Meta
   shows it only once; if you lose it, generate a new one.

!!! warning "Keep the token secret"
    Anyone with this token can send WhatsApp messages as your business. Paste it
    only in GoodBards, never in an email or a chat.

## How to connect in GoodBards

1. Open your account menu (your picture, top right), then choose **Connections**.
2. On the **Messaging** tab, find **WhatsApp** and choose **Connect**.

    ![The Messaging tab with the WhatsApp card](../../../img/screenshots/whatsapp/15-goodbards-tile.png)

3. Paste the four details (see the table above) and choose **Connect WhatsApp**.

GoodBards checks everything with Meta before saving. If Meta refuses, nothing is
saved and the message says which detail is wrong: see **If it does not work**
below. Once connected, the card shows your business name, your number and your
WhatsApp profile picture (or your initials when you have none); **Number &
webhook** shows Meta's quality rating.

![The connected WhatsApp card: business name, number, Number & webhook](../../../img/screenshots/whatsapp/19-goodbards-connected.png)

## How to receive delivery updates and replies

Meta tells GoodBards when a message is delivered or read, and when someone replies
or asks to stop, through a **webhook**. You set it once:

1. In GoodBards, on the WhatsApp card, choose **Number & webhook** and copy the
   **Callback URL** and **Verify token**.
2. In your Meta app, open **WhatsApp → Configuration → Webhook → Edit**, paste
   both, and choose **Verify and save**.
3. Under **Webhook fields**, subscribe to **messages** and
   **message_template_status_update**.

## If it does not work

GoodBards shows Meta's refusal in plain words, with Meta's own text in brackets.

| GoodBards says | Why | What to do |
| --- | --- | --- |
| **Meta cannot find this WhatsApp Business Account or phone number with this token. Most often the system user has no access to the account…** (Meta: *Object with ID … does not exist, cannot be loaded due to missing permissions*) | Most often: the system user has no access to the WhatsApp account. Or an ID was mistyped. | Do step **4b**: Messaging accounts → your account → People → your system user with **Everything**. Check both IDs. Then choose **Connect WhatsApp** again; the same token works. |
| **The access token is not valid or has expired** | The token was copied incompletely, revoked, or set to expire. | Generate a new token (step 4c) with expiry **Never**, and paste it again. |
| **The app secret does not belong to the app that created this token** | The secret comes from another app, or the token was generated for another app. | Copy the secret from the app you picked in step 4c (App settings → Basic). |
| **The token is missing a permission** | One of the two permissions was not ticked. | Generate a new token with **whatsapp_business_management** and **whatsapp_business_messaging**. |
| **The phone number ID is a number…** | The phone number itself was pasted. | Paste the **Phone Number ID** shown next to the number (step 2). |
| **This phone number ID is not part of this WhatsApp Business Account** | The two IDs come from different accounts. | Copy both from the same place (step 2). |

## Good to know

- **Meta bills you**, per marketing message, at Meta's rate for the recipient's
  country. Add a payment method in WhatsApp Manager before sending from your real
  number.
- **The test number** can only message a few phone numbers that you add in Meta
  (up to 5). Use it to try things, not for campaigns.
- **Quality rating.** Meta rates your number from how people react to your
  messages. A low rating lowers how many people you can message per day: only
  message contacts who agreed.
- **Consent.** GoodBards only sends to contacts with WhatsApp consent, and a
  "STOP" reply withdraws it.
- To use a new token or number, choose **Connect** again with the new details:
  your webhook keeps working.

## How to disconnect

1. On the WhatsApp card, choose **Disconnect**.
2. GoodBards forgets the token and app secret. Nothing changes in your Meta
   account; to stop the key completely, remove the system user's token in
   Business settings (**Revoke tokens**).

---

*Still stuck? [Contact support](../../contact.md).*
