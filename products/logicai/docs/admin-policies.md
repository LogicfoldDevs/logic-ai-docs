---
title: Policies
description: Control which tools Logic AI can use and configure per-user overrides.
---

The Policies tab controls what Logic AI can and cannot do in your org. This is where you define tool permissions, model access, and approval workflows.

## How Policies Work

Logic AI uses a layered policy system:

1. **Org default policy** — Applies to all users unless overridden
2. **Per-user overrides** — Grant or restrict specific tools for individual users

When a user starts a chat, Logic AI resolves their effective policy by checking for a user-specific override first, then falling back to the org default.

## Tool Permissions

Each tool can be individually enabled or disabled:

| Tool | What it does | Default |
|---|---|---|
| SOQL Query | Run read queries against any object | Enabled |
| Describe Object | Inspect object schema and fields | Enabled |
| Get Record | Retrieve a single record by ID | Enabled |
| Create Record | Create new records | Disabled |
| Update Record | Modify existing records | Disabled |
| Delete Record | Delete records (sends to Recycle Bin) | Disabled |
| Mass Create | Bulk-create multiple records | Disabled |
| Mass Update | Bulk-update multiple records | Disabled |

Disabling a tool removes it from Logic AI's available actions entirely — it won't suggest or attempt to use it.

## Model Allowlist

You can restrict which AI models are available in your org. By default, Logic AI uses the model configured in Settings, but policies can allow users to switch between approved models.
