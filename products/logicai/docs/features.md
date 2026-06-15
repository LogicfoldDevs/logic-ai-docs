---
title: Features
description: What Logic AI can do for you and how to use it — for everyday users.
---

Logic AI is an AI assistant that lives right inside Salesforce. Ask it a question in plain English and it works with your records to get things done — finding information, building reports, drafting emails, and more. Everything it does runs as *you*, so it can only see and change what you already have permission to.

This page is for everyday users. Admins configuring what's available should see the [Admin Console](/products/logicai/docs/admin-dashboard) pages.

## Getting answers about your data

Just ask. Logic AI understands your org's objects and fields, so you can say things like:

- *"How many open opportunities do I have closing this month?"*
- *"Show me the contacts at Acme and their last activity."*
- *"Which cases have been open more than a week?"*

It figures out the right query, runs it with your permissions, and shows you the results — no report builder required. You can also ask it to **search across everything** when you're not sure where something lives (*"find anything mentioning the Henderson contract"*).

## Taking action

Beyond reading data, Logic AI can do work for you. Depending on what your admin has enabled, it can:

- **Manage records** — create, update, and delete records, one at a time or in bulk
- **Work with reports** — run a report you already have, or build a new one
- **Communicate** — send an email, send a notification to other users, or post to Chatter on a record or group
- **Run your org's automations** — launch Flows and Apex actions
- **Export results** — produce a CSV file or a formatted PDF report

For anything sensitive — sending an email, deleting records, and others your admin chooses — Logic AI pauses and asks you to approve before it happens, showing you exactly what it's about to do. The [Tools reference](/products/logicai/docs/tools) lists every tool in detail.

## Working with files

Attach or point Logic AI at a file on a record — a PDF, image, text file, or other type — and it can read the contents to summarize it or answer questions about it.

## Interactive prompts

When Logic AI needs you to make a choice before continuing, it shows **clickable options** right in the chat, so you can just pick one instead of typing out your answer.

## Blueprints — save and reuse your work

When you've worked through something useful, save it as a **Blueprint** and run the same workflow again later without re-explaining it.

- **Save a chat** — after a useful conversation, use the **Save chat** chip. Logic AI reviews what you did and distills it into a draft Blueprint with a suggested name and instructions, which you can edit before saving.
- **New Blueprint** — write one from scratch with a name, a short description of when to use it, and the steps.
- **Refine with Logic AI** — while editing, add a note like *"focus on the email step, drop the dashboard part"* and re-distill to rework the instructions.

Your saved Blueprints appear as **chips above the chat box** — click one to run it. You can type a detail first (like an account name) and then click the chip to combine your input with the saved steps.

Each Blueprint is **private by default**. Turn on **Share with everyone in the org** to make it available to all Logic AI users; only you (or an admin) can edit or delete one you own. Admins can review and manage every Blueprint from the [Blueprints](/products/logicai/docs/admin-blueprints) tab.

Running a Blueprint doesn't bypass any safeguards — it runs its steps in your user context, with the same permissions and approvals as any other chat.

## Memory

When memory is enabled for your org, you can tell Logic AI to **remember** facts and preferences (*"remember that I manage the West region"*) and it will recall them in future conversations.

## Feedback

You can react to individual answers with 👍 / 👎 and raise a support ticket directly from the chat — see [Feedback and reactions](/products/logicai/docs/feedback-and-reactions).
