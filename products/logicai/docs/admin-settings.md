---
title: Settings
description: Gateway connection, default model, and feature flags.
---

The Settings tab is your gateway configuration page. This is the first tab you'll see after installing Logic AI if the gateway hasn't been connected yet.

## Gateway Connection

The top section shows your connection status:

- **Connected** (green) — Your org is linked to the Logicfold gateway
- **Not connected** (red) — No active connection. Use **Request access** or **I have a claim code** to set up

### Connecting

There are two ways to connect. Both open a Logicfold authorization window and require accepting the **Logic AI Service Agreement**.

**Request access** — start fresh from inside Salesforce:

1. Click **Request access**
2. In the window, enter your email and organization name, and accept the service agreement
3. Click **Request access** — the window closes and your status turns green

Requesting access links your org, but chat isn't live until Logicfold provisions your private AI workspace. You'll receive an email when chat is ready (usually within a few minutes).

**I have a claim code** — if you signed up on the Logicfold website first:

1. Click **I have a claim code**
2. Enter the claim code from your welcome email (`CLAIM-XXXXXXXX`) and accept the service agreement
3. Click **Connect** — the window closes and your status turns green

Because your workspace is already provisioned, chat is ready immediately.

If you've connected before, the button reads **Reconnect** and re-uses the org name and email already on file.


### Disconnecting

Click **Disconnect** to revoke the gateway token immediately. This stops all Logic AI conversations in your org until you reconnect. Use this if you suspect the token has been compromised or if you're decommissioning Logic AI.

## Default Model

Select the AI model used for conversations. More capable models produce better results but consume more credits per interaction. Your Logicfold representative can advise on the best model for your use case.

## Feature Flags

- **Chatbot Enabled** — Master on/off switch for Logic AI. When disabled, users see a "temporarily unavailable" message instead of the chat interface.
