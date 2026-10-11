# Use GoodBards from your AI assistant (MCP)

Work with GoodBards from the AI assistant you already use, such as Claude: ask
your GoodBards agents to write or research, read your social and campaign
reports, without opening GoodBards.

## What MCP is

MCP (Model Context Protocol) is a standard way for an AI assistant to use outside
tools. GoodBards offers an MCP server: once your assistant is connected, it can
call GoodBards' tools for you, with your company's brand and data.

## What your assistant can do

What it can do depends on the permissions (scopes) you grant when you connect:

| Permission | Tools |
| --- | --- |
| **agents:invoke** (always) | List your GoodBards agents, and ask one to write, research or analyse. |
| **reports:read** | Read your social accounts and reports, Google Analytics reports, campaigns and content. |
| **reports:write** | Start a new social report. |
| **content:write** | Save a new piece of content, and schedule a post. |

Grant only what you need. With **agents:invoke** alone, the assistant can talk to
your agents but cannot read reports or create content.

## 1. Prepare the connection in GoodBards

A company administrator does this once.

1. Open **Tenant Settings → Security**, and create an **API key** for the
   assistant. See [Use the GoodBards API](use-the-api.md).
2. On that key, choose **OAuth Apps**, then **Create OAuth App**. Give it a name,
   for example *Claude AI Connector*.
3. Copy the **Client ID** and the **Client Secret**. The secret is shown only
   once.

## 2. Connect your assistant

In your assistant's connector settings (in Claude: **Settings → Connectors → Add
custom connector**):

| Setting | Value |
| --- | --- |
| **Server URL** | `https://mcp.goodbards.ai/mcp` |
| **Client ID** | From step 1 |
| **Client Secret** | From step 1 |

The assistant opens a GoodBards page asking you to **Allow** the access. Once you
allow it, the tools appear in your assistant.

Developers can instead send the API key directly, as
`Authorization: Bearer <your API key>`; the assistant then gets the agent tools
only.

## 3. Use your agents

Ask in plain words, for example:

- *"List my GoodBards agents."*
- *"Ask the Brand Marketing Agent for three LinkedIn post ideas about our
  festive gifting guide."*
- *"Get the latest LinkedIn report for Tropika Home and summarise it."*

To continue a conversation with the same agent, keep asking in the same chat:
the assistant reuses the session.

## 4. Stay in control

- **Everything happens in your company.** The connection belongs to one company
  and acts as the administrator who created the OAuth app.
- **Check before anything is saved or scheduled.** With **content:write**, ask
  the assistant to show you the content before it saves it or schedules a post.
- **Disconnect at any time:** delete the OAuth app, or revoke the API key, on the
  **Security** tab. The assistant loses access straight away.

## Good to know

- **Access tokens last an hour** and renew on their own for up to 30 days; after
  that, allow the access again.
- **Your agents work as in GoodBards**, with your brand voice and knowledge, and
  their usage counts toward your plan.
