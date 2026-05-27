---
title: Quickstart Guide
order: 1
---

# Quickstart Guide

Get LogicAI running in your Salesforce org in under 5 minutes.

## Step 1: Install the Package

Your Logicfold representative will provide an installation link. Click it, choose **Install for All Users**, and wait for the confirmation email.

After installation you'll land on a post-install page — you can also find LogicAI under **Setup > Installed Packages** at any time.

## Step 2: Open the Admin Console

Go to the **App Launcher** (the waffle icon) and search for **Logic AI Admin**. Click it to open the admin console. If this is a fresh install, you'll land directly on the **Settings** tab.

## Step 3: Connect to Logicfold

On the **Settings** tab, click **Connect to Logicfold**. A popup will open:

1. Enter your email address
2. Optionally enter your organization name
3. Click **Connect**

The popup closes automatically and the Settings tab will show a green **Connected** status. Your org now has a secure, encrypted connection to the LogicAI gateway.

## Step 4: Assign Permission Sets

Assign the appropriate permission set to each user:

| Permission Set | Who gets it | What it grants |
|---|---|---|
| **Agentfold Admin** | Salesforce admins managing LogicAI | Full access to admin console, settings, policies, logs |
| **Agentfold User** | End users chatting with LogicAI | Access to the chat interface and standard AI tools |

Go to **Setup > Permission Sets**, click the permission set, then **Manage Assignments > Add Assignment**.

The installing admin is automatically assigned Agentfold Admin during installation.

## Step 5: Add LogicAI to a Page

1. Navigate to any record page (e.g., an Account)
2. Click the **gear icon > Edit Page** to open Lightning App Builder
3. Find **logicAI** in the component palette and drag it onto the page
4. Save and Activate

## Step 6: Start Chatting

Open any record page where you added the component. The LogicAI chat panel appears on the right side. Try:

- **"Show me all contacts at this account"** — queries related records
- **"What open opportunities do I have closing this month?"** — filters by your user and date
- **"Create a task to follow up with this contact next Tuesday"** — creates records with context
- **"Summarize the recent activity on this account"** — reads and synthesizes data
- **"Update this opportunity stage to Closed Won"** — modifies the current record

LogicAI sees the record you're on, respects your Salesforce permissions, and can work with any standard or custom object in your org.

## What's Next

- **[Admin Console](/docs/admin-settings)** — Configure the gateway, models, and feature flags
- **[Policies](/docs/admin-policies)** — Control which tools are available and to whom
- **[Tools Reference](/docs/tools)** — Full list of what LogicAI can do
- **[FAQ](/docs/faq)** — Common questions and troubleshooting
