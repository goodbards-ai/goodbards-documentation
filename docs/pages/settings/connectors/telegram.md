# Telegram

Post to your Telegram channels and send personal Telegram messages to your
contacts, from your campaigns.

## What it's for

Telegram reaches people where they already chat. With the **Telegram**
connector, a campaign can:

- **Post to a channel**: one post in your Telegram channel or group, seen by
  every subscriber.
- **Message contacts**: a personal message to each contact who subscribed to
  your updates on Telegram, with their first name filled in.

Everything goes through **your own Telegram bot**: messages come from your
brand's name and picture, never from GoodBards.

## Before you start

- Telegram is included in the **Pro** and **Full** plans.
- You must be an **administrator** or the **owner** of your GoodBards company
  account.
- You need a Telegram account on your phone or computer, to create the bot.
- To post to a channel, you need a Telegram channel (or group) where you are an
  administrator.

## How to create your bot

You do this once, in Telegram. It takes two minutes.

1. In Telegram, search for **@BotFather** (the official account, with a blue
   tick) and open a chat with it.
2. Send `/newbot`.
3. Send the name people will see, for example your brand name.
4. Send a username for the bot. It must end in `bot`, for example
   `yourbrand_news_bot`.
5. BotFather answers with a **token**, a long code such as
   `123456789:AAH…`. Copy it. Keep it private: anyone with it can send
   messages as your bot.

To give the bot your logo and a description, send `/setuserpic` and
`/setdescription` to BotFather.

## How to connect

1. Open your account menu (your picture, top right), then choose **Connections**.
2. On the **Messaging** tab, find **Telegram** and choose **Connect**.
3. Paste the token from BotFather and confirm. GoodBards checks it with
   Telegram before saving. If Telegram refuses it, nothing is saved.

The card then shows your bot's name, and a line counting your Telegram contacts
(see below).

## How to post to a channel

1. In Telegram, open your channel, then **Administrators → Add Admin**, and add
   your bot. Give it the right to post messages.
2. Back in GoodBards, on the Telegram card, choose **Channels**. The channel
   appears with **Can post**. If it does not, type its `@name` in the box and
   choose **Add**.
3. In a campaign, add a **Telegram** tactic, keep **Post to a channel**, write
   your message and publish or schedule it to that channel.

## How to message your contacts

A Telegram bot can only write to people who started a chat with it first.
Each contact gets a **personal link**: when they open it on their phone and tap
**Start**, their Telegram account is linked to their contact record and their
consent is recorded.

### 1. Get your contacts to subscribe

Pick what fits:

| Way | When to use it |
| --- | --- |
| **Email invitation** | Many contacts at once. In the email editor, drag the **Telegram invite** block (Components) into an email: it has a **Join us on Telegram** button and a QR code, both with each contact's own link. Send it like any email campaign. |
| **QR code** | Someone in front of you, at an event or in a meeting. Open their contact page; in **Messaging consent**, next to Telegram, choose **QR code** and let them scan it with their phone camera. |
| **Email link** | One person. On their contact page, choose **Email link**: your own mail app opens with a short message and their link, ready to send. |
| **Copy link** | Anywhere else (a chat, a message). Paste it to that person only: each link belongs to one contact. |

!!! tip "On a phone"
    The link opens Telegram, where the contact taps **Start**. On a computer
    without Telegram installed, it cannot be started: that is why the email
    block and the contact page also show a QR code to scan with the phone.

### 2. Send the message

1. In a campaign, add a **Telegram** tactic.
2. Under **Who receives it**, choose **Message contacts**.
3. In **Recipients**, choose contacts, segments or mailing lists. The box above
   tells you how many can be reached, and why the others cannot (not on
   Telegram yet, no Telegram consent, marked do not contact).
4. Write your message. **Personalize** adds the contact's first name, last name
   or job title.
5. Publish or schedule it to **Contacts of this tactic**. Messages go out over
   the next minutes. Publishing the same message again only sends it to
   contacts who did not get it yet, or whose message failed.

On the tactic page, **Delivery status** lists every message: sent, clicked, or
the reason it failed. Each message sent, each click and each opt-out also
appears on the contact's timeline.

## What you see in reports

| | Channel post | Personal messages |
| --- | --- | --- |
| Sent | Posts published | Messages sent |
| Clicks | Link clicks (people only) | Link clicks (people only) |
| Reactions | Reactions on your posts | — |
| Subscribers | Members of the channel | — |
| Failed / opt-outs | — | Messages Telegram refused; contacts who blocked your bot |

Telegram does not tell bots who **read** a message or how many people
**viewed** a channel post, so those show "—".

## Good to know

- **Stopping is always possible.** A contact who sends `/stop` to your bot, or
  blocks it, stops receiving messages: their Telegram consent is withdrawn
  automatically. Sending `/start` again subscribes them back.
- **Consent is per channel.** Telegram consent is separate from email
  consent; you see both on the contact page under **Messaging consent**.
- **Personalize in channel posts.** First name and the other fields are only
  filled in personal messages. In a channel post they are left out.
- The Telegram card shows **subscribed**, **invited** (link created, Start not
  tapped yet) and **blocked** counts.
- The bot's automatic replies (after **Start** or `/stop`) are in the
  language of the contact's Telegram app, in any of GoodBards' 13 languages;
  English otherwise. Your own messages are sent exactly as you write them.

## How to disconnect

1. On the Telegram card, choose **Disconnect**.
2. GoodBards forgets the token. Your bot, channels and subscribers stay as they
   are in Telegram; connect the same bot again to carry on.

---

*Still stuck? [Contact support](../../contact.md).*
