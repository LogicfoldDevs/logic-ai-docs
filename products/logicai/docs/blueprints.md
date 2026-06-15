---
title: Blueprints
description: Save a chat as a reusable workflow you can run again — privately or shared with your team.
---

A **Blueprint** is a saved, reusable workflow. When you've worked through something useful with Logic AI — pulling a report, drafting an email, updating a set of records — you can save those steps as a Blueprint and run the same thing again later without re-explaining it.

Blueprints are tool-agnostic instructions, not a recording. Running one tells Logic AI *what to accomplish*, and it carries out the steps against your current data with all the usual permissions and approvals in place.

## Creating a Blueprint

There are two ways to create one, both from the chat panel:

- **Save a chat** — after a useful conversation, use the **Save chat** chip. Logic AI reviews the conversation (including the steps it took) and distills it into a draft Blueprint with a suggested name, description, and instructions. You review and edit the draft before saving.
- **New Blueprint** — write a Blueprint from scratch by giving it a name, an optional one-line description of when to use it, and the instructions.

When editing a draft, you can also **refine it with Logic AI** — type a note like *"focus on the email step, drop the dashboard part"* and re-distill to rework the instructions.

## Running a Blueprint

Your saved Blueprints appear as **chips above the chat composer**. Click one to run it. You can also type a few details first (for example, an account name) and then click the chip — Logic AI combines your input with the Blueprint's steps.

## Sharing

Each Blueprint is **private by default** — visible only to you. Turn on **Share with everyone in the org** to make it available to every Logic AI user. Shared Blueprints show up in everyone's chip list, but only the owner (or an admin) can edit or delete them.

## Managing Blueprints as an admin

The **Blueprints** tab in the admin console lists every Blueprint in the org — both private and shared. From there an admin can review the full instructions, edit, change sharing, or delete any Blueprint, alongside how many times each has been used.

## Security

Blueprints don't bypass any of Logic AI's safeguards. Running a Blueprint executes its steps in your user context — the same [sharing rules, field-level security, tool permissions, and approval requirements](/products/logicai/docs/tools#security-model) apply as in any other chat. A Blueprint can only do what you could already ask Logic AI to do directly.
