# 🛠️ Developer Guide

This guide provides everything developers need to integrate **Good Bards** into their workflows — including authentication, API usage, webhooks, and best practices.

---

## 🔑 Authentication

All API requests must be authenticated using a **Bearer token**.

### 🔐 How to Authenticate

1. Obtain your API token from `Settings > API Keys`
2. Include it in the `Authorization` header:

```http
Authorization: Bearer YOUR_API_TOKEN
```

Explore: [Authentication API](../api/authentication.md)

---

## 🧾 API Overview

The Good Bards REST API gives you programmatic access to:

- 📁 Assets & versions  
- 📄 Campaigns & documents  
- 🗃️ Folders & organization  
- 📈 Analytics & reports  
- 🔄 Webhooks and automations  

Explore: [API Reference](../api/authentication.md)

---

## 📂 Example: Create a New Asset

```http
POST /v1/{tenantId}/assets
Content-Type: application/json
Authorization: Bearer YOUR_API_TOKEN
```

```json
{
  "title": "New Product One-Pager",
  "folder": "/Q4/Launch",
  "assetType": "document",
  "content": {
    "blocks": [
      { "type": "text", "value": "Welcome to our launch!" }
    ]
  }
}
```

Explore: [Assets API](../api/assets.md)

---

## 📡 Webhooks

Webhooks let you receive real-time notifications for platform events like:

- `asset.published`
- `campaign.created`
- `asset.updated`
- `webhook.failed`

### 🔧 Setting Up Webhooks

1. Go to `Settings > Webhooks`
2. Register your endpoint URL
3. Choose the events you want to subscribe to

Webhook payloads are sent as `POST` requests with a JSON body and HMAC-SHA256 signature.

Explore: [Webhooks API](../api/webhooks.md)

---

## 🧠 Use Cases

- Sync assets with an external DAM or CMS  
- Trigger internal approval workflows  
- Monitor campaign publishing status  
- Build analytics dashboards with raw campaign data  

---

## 🧩 Platform Integrations

Use Connectors to link your dev stack to Good Bards:

- ✅ Google Drive, Dropbox  
- ✅ Slack, Discord  
- ✅ Webhooks & Custom APIs  

Explore: [Connectors](../features/connectors.md)

---

## 🚧 Rate Limits

- **Standard Plan**: 60 requests/minute  
- **Pro Plan**: 200 requests/minute  
- **Burst**: Limited to 5 concurrent API calls per token  

For bulk operations, use batch endpoints or asynchronous processing.

---

## 🧪 Testing & Staging

A sandbox environment is available on request. It mirrors production behavior but doesn't affect real data or metrics.

!!! info
    Contact support to request sandbox access or to rotate API keys.

---

## 📬 Support & Docs

Need help? We offer:
- [Full API reference](../api/authentication.md)  
- [Contact support](../contact.md)  
- Postman collections (coming soon)  

You can also join our developer Slack by request.
