---
title: Quickstart Guide
description: Get Logic AI running in your Salesforce org in a few minutes.
---

Get Logic AI running in your Salesforce org in a few minutes.

## Step 1: Install the Package

Your Logicfold representative will provide an installation link. Click it, choose **Install for Admins Only**, and wait for the confirmation email.

After installation you'll land on a post-install page — you can also find Logic AI under **Setup > Installed Packages** at any time.

## Step 2: Open the Admin Console

Go to the **App Launcher** (the waffle icon) and search for **Logic AI Admin**. Click it to open the admin console. If this is a fresh install, you'll land directly on the **Settings** tab.

## Step 3: Connect to Logicfold

On the **Settings** tab, the **Logicfold connection** card shows a **Not connected** status. There are two ways to connect, depending on how you signed up.

### Option A — Request access

Use this if you're starting fresh from inside Salesforce.

1. Click **Request access**. A Logicfold authorization window opens.
2. Enter your **email** and **organization name**.
3. Read and accept the **Logic AI Service Agreement** (checkbox).
4. Click **Request access**.

The window closes and your connection status turns green. Your org now has a secure, encrypted link to the Logic AI gateway.

> **Heads up:** Requesting access connects your org, but chat isn't live yet. Logicfold is automatically notified to provision your private AI workspace. **You'll get an email when chat is ready** — usually within a few minutes. Until then, the chat panel shows a "being provisioned" message.

### Option B — I have a claim code

Use this if you signed up for Logic AI on the [Logicfold website](https://www.logicfold.com/products/logicai) first. Your workspace is already provisioned, so this path connects you instantly — no waiting for activation.

1. Click **I have a claim code**. A Logicfold authorization window opens.
2. Enter the **claim code** from your welcome email (format `CLAIM-XXXXXXXX`).
3. Read and accept the **Logic AI Service Agreement** (checkbox).
4. Click **Connect**.

The window closes and your connection status turns green. Because your workspace was already activated, chat is ready to use immediately.

## Step 4: Assign Permissions

Assign the appropriate permissions to each user:

| Permission Set | Who gets it | What it grants |
|---|---|---|
| **Admin** | Salesforce admins managing Logic AI | Full access to admin console, settings, policies, logs |
| **User** | End users chatting with Logic AI | Access to the chat interface and standard AI tools |

Go to **Logic AI Admin > Users**, and add the permissions for the users there.

The installing admin is automatically assigned Admin during installation.

## Step 5: Start Chatting

Go to the **App Launcher** (the waffle icon) and search for **Logic AI**. The Logic AI chat panel appears. Try:

- **"Show me all contacts at this account"** — queries related records
- **"What open opportunities do I have closing this month?"** — filters by your user and date
- **"Create a task to follow up with this contact next Tuesday"** — creates records with context
- **"Summarize the recent activity on this account"** — reads and synthesizes data
- **"Update this opportunity stage to Closed Won"** — modifies the current record

> If chat shows a "being provisioned" message after using **Request access**, your workspace is still being set up. Wait for the activation email, then try again.

## What's Next

- **[Admin Console](/docs/admin-settings)** — Configure the gateway, models, and feature flags
- **[Policies](/docs/admin-policies)** — Control which tools are available and to whom
- **[Tools Reference](/docs/tools)** — Full list of what LogicAI can do
- **[FAQ](/docs/faq)** — Common questions and troubleshooting
