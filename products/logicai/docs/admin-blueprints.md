---
title: Blueprints
description: Review and manage the reusable workflows users have saved across the org.
---

A **Blueprint** is a saved, reusable workflow — a set of tool-agnostic instructions a user can run again in chat without re-explaining it. Users create Blueprints themselves from the chat panel (see [Features](/products/logicai/docs/features#blueprints-save-and-reuse-your-work)); the **Blueprints** tab in the admin console is where you oversee them org-wide.

## The Blueprints tab

The tab lists every Blueprint in the org — both **private** ones (owned by a single user) and **shared** ones (visible to everyone). Each row shows:

- **Blueprint** — name and description
- **Created by** — the owner
- **Sharing** — private or shared with the org
- **Uses** — how many times it has been run, and when it was last used
- **Created** — when it was saved

Expand any row to read its full instructions.

## What admins can do

- **Review** the instructions of any Blueprint, including private ones owned by other users
- **Edit** a Blueprint's name, description, or instructions
- **Change sharing** — make a Blueprint shared (visible to all users) or private again
- **Delete** any Blueprint

Outside the admin tab, a regular user can only edit or delete Blueprints they own. Admins can manage any Blueprint in the org.

## Sharing model

Blueprints are **private by default** — visible only to their creator. A shared Blueprint appears in every Logic AI user's chip list, ready to run. Sharing changes only visibility; running a Blueprint always executes in the *running* user's context, with their permissions, field-level security, and approval requirements enforced — a shared Blueprint can't let anyone do something they couldn't already ask Logic AI to do directly.
