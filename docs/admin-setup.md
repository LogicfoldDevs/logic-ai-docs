---
title: Admin Setup
order: 2
---

# Admin Setup

This guide walks through configuring LogicAI for your organization.

## Permission Sets

LogicAI ships with two permission sets:

- **Admin** — Full access to the admin console, settings, policies, logs, and gateway configuration. Assign to Salesforce admins who will manage LogicAI.
- **User** — Access to the chat interface and standard AI tools. Assign to end users who will interact with LogicAI.

## Connecting to Logicfold

1. Open the **LogicAI Admin** tab
2. Click **Connect to Logicfold**
3. A popup will open — enter your email and organization name
4. Once connected, LogicAI will display a green "Connected" status

The connection uses a secure Named Credential. Your API token is stored encrypted and is never visible in Apex code.

## Policies

Policies let you control which tools LogicAI can use and what models it runs on. Navigate to the **Policies** tab in the admin console to:

- Enable or disable specific tools (SOQL queries, record creation, record updates, etc.)
- Set the default AI model
- Configure per-user or per-profile overrides
- Enable memory features

## Adding LogicAI to Record Pages

1. Open the **Lightning App Builder** for any record page
2. Drag the **logicAI** component onto the page
3. Save and activate

LogicAI will automatically have context about the record the user is viewing.

## Settings

The **Settings** tab in the admin console lets you configure:

- **Streaming** — Enable or disable real-time streaming responses
- **Max Turns** — Maximum number of tool-use rounds per conversation turn (default: 8)
- **Memory** — Enable user memory and org-wide memory features
