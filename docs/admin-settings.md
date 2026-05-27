---
title: "Admin: Settings"
order: 10
---

# Settings

The Settings tab is your gateway configuration page. This is the first tab you'll see after installing LogicAI if the gateway hasn't been connected yet.

## Gateway Connection

The top section shows your connection status:

- **Connected** (green) — Your org is linked to the Logicfold gateway and ready to use
- **Disconnected** (red) — No active connection. Click **Connect to Logicfold** to set up

### Connecting

1. Click **Connect to Logicfold**
2. A popup opens — enter your email and organization name
3. The gateway validates your org and provisions a secure workspace
4. On success, the popup closes and your connection status turns green

The connection is secured via a Named Credential with an encrypted bearer token. The token is never visible in Apex code and can only be used for authorized callouts to the LogicAI gateway.

### Disconnecting

Click **Disconnect** to revoke the gateway token immediately. This stops all LogicAI conversations in your org until you reconnect. Use this if you suspect the token has been compromised or if you're decommissioning LogicAI.

## Default Model

Select the AI model used for conversations. More capable models produce better results but consume more credits per interaction. Your Logicfold representative can advise on the best model for your use case.

## Feature Flags

- **Chatbot Enabled** — Master on/off switch for LogicAI. When disabled, users see a "temporarily unavailable" message instead of the chat interface.
- **Streaming Enabled** — When on, responses appear in real-time as the AI generates them. When off, users see a loading spinner until the full response is ready. Streaming must be enabled for write operations (create, update, delete records).

## Max Turns

The maximum number of tool-use rounds per conversation turn. Each "turn" is one cycle of: user sends a message, AI responds, optionally uses tools, and responds again. Default is 8. Higher values allow more complex multi-step operations but cost more credits.
