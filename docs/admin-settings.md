---
title: Settings
description: Gateway connection, default model, and feature flags.
---

The Settings tab is your gateway configuration page. This is the first tab you'll see after installing Logic AI if the gateway hasn't been connected yet.

## Gateway Connection

The top section shows your connection status:

- **Connected** (green) — Your org is linked to the Logicfold gateway and ready to use
- **Disconnected** (red) — No active connection. Click **Connect to Logicfold** to set up

### Connecting

1. Click **Connect to Logicfold**
2. A popup opens — enter your email and organization name
3. The gateway validates your org and provisions a secure workspace
4. On success, the popup closes and your connection status turns green


### Disconnecting

Click **Disconnect** to revoke the gateway token immediately. This stops all Logic AI conversations in your org until you reconnect. Use this if you suspect the token has been compromised or if you're decommissioning Logic AI.

## Default Model

Select the AI model used for conversations. More capable models produce better results but consume more credits per interaction. Your Logicfold representative can advise on the best model for your use case.

## Feature Flags

- **Chatbot Enabled** — Master on/off switch for Logic AI. When disabled, users see a "temporarily unavailable" message instead of the chat interface.
