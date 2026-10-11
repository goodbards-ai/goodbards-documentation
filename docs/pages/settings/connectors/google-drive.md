# Google Drive

Use files from your Google Drive in GoodBards.

## What it's for

The **Google Drive** connector lets you bring Drive files into GoodBards:

- **Attach Drive files to an AI agent conversation.** In the agent chat, open the
  attachments menu and choose **Google Drive**. Google's own file picker opens:
  select one or several files, including from shared drives. See
  [Chat agents](../../agentic-ai/chat-agents.md).
- **Keep a Drive folder in sync** with your Content Repository, with a **Drive
  sync** task in the [Scheduler](../../tool-box/scheduler.md).

## Before you start

- You must be an **administrator** or the **owner** of your GoodBards company
  account to connect it.
- Use the Google account that holds, or has access to, the files.

## How to connect

1. Open your account menu (your picture, top right), then choose **Connections**.
2. On the **Storage** tab, find **Google Drive** and choose **Connect**.
3. Pick your Google account and accept the permissions.
4. You are taken back to GoodBards. The card shows the account name.

Until it is connected, the agent chat shows **Google Drive (Not connected)**.

## How to sync a Drive folder

1. Open the [Scheduler](../../tool-box/scheduler.md) and create a task of type
   **Drive sync**.
2. Fill in:
    - **Google Drive folder ID**: the last part of the folder's address in Drive.
    - **Google Drive folder name** (optional).
    - The destination folder in your Content Repository.
3. Choose how often it runs, then save.

## What GoodBards does with it

| GoodBards… | Details |
| --- | --- |
| **Reads** | The files you pick, and the files of the folder you sync. |
| **Converts** | Google Docs, Slides and Drawings into PDF, and Google Sheets into Excel, when it brings them in. |
| **Does not** | Create, change or delete anything in your Drive. |

## Good to know

- **Folders cannot be picked** in the agent chat — pick the files inside.
- **GoodBards only sees what you give it through Google's file picker.** If a
  synced folder seems to miss files, open the picker and select those files
  once: Google then lets GoodBards read them.
- **Imported files are copies.** Changing the file in Drive later does not change
  the copy in GoodBards, unless a Drive sync task brings it in again.

## How to disconnect

1. On the Google Drive card, choose **Disconnect**.
2. Confirm.

Files already brought into GoodBards stay there. To remove access on Google's
side too, do it from your Google Account, under third-party connections.

---

*Still stuck? [Contact support](../../contact.md).*
