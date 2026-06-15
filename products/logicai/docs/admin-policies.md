---
title: Policies
description: Control which tools Logic AI can use and configure per-user overrides.
---

The Policies tab controls what Logic AI can and cannot do in your org. This is where you define tool permissions, per-call limits, approval requirements, and which models users can pick.

## How Policies Work

Logic AI uses a layered policy system:

1. **Org default** — Applies to every chat user
2. **Per-user overrides** — Take precedence over the org default for individual users

When a user starts a chat, Logic AI resolves their effective policy by checking for a user-specific override first, then falling back to the org default.

## Tool Permissions

Tools are grouped into **Reading data**, **DML**, and **Utilities**. Each tool can be individually toggled on or off:

| Tool | What it does | Default |
|---|---|---|
| SOQL query | Run read queries against any object | Enabled |
| Get record | Retrieve a single record by ID | Enabled |
| Describe object | Inspect object schema and fields | Enabled |
| Create record | Create new records | Disabled |
| Update record | Modify existing records | Disabled |
| Delete record | Delete records (sends to Recycle Bin) | Disabled |
| Mass create records | Bulk-create multiple records | Disabled |
| Mass update records | Bulk-update multiple records | Disabled |
| Mass delete records | Bulk-delete multiple records | Locked — contact Logicfold |
| Generate CSV | Build a CSV file and attach it to the chat | Disabled |
| Generate PDF | Compose a formatted report in the side panel | Disabled |
| SOSL search | Search a term across multiple objects at once | Disabled |
| Send email | Send an email on the user's behalf | Disabled |
| Send notification | Send a Salesforce custom notification | Disabled |
| Post to Chatter | Post an update to a record feed or group | Disabled |
| Run report | Run an existing report and return results | Disabled |
| Create report | Build a new report definition | Disabled |
| Invoke Apex action | Call an invocable Apex action | Disabled |
| Invoke Flow | Launch an autolaunched Flow | Disabled |

Disabling a tool removes it from Logic AI's available actions entirely — it won't suggest or attempt to use it.

## Per-Call Limits

Some tools expose a **Max per call** limit:

- **SOQL query** — maximum rows returned (default 50, up to 2,000)
- **Mass create / update / delete records** — maximum records per operation (default 200, up to 10,000)

## Approval Requirements

Write tools can require the user to approve the action in-chat before it runs:

- **Create record / Update record / Mass create / Mass update** — approval is configurable (toggle "Needs approval")
- **Send email** — approval is **required by default** (configurable); Logic AI shows the recipients, subject, and body before sending
- **Delete record / Mass delete records** — approval is **always required** and cannot be turned off

## Model Allowlist

The **Models** section controls which Anthropic models the chat model picker exposes. Toggle individual models on or off. Leaving all models on means no restriction (users see the full picker).

## Per-User Overrides

Below the org default, every user assigned the **Logic AI User** permission set is listed (admins are excluded). Click a user to open their override editor, where you can:

- Enable or disable individual tools just for that user
- Adjust their per-call limits and approval requirements
- Restrict the models they can pick

Each user shows whether they **inherit the org default** or are **customized**. Use **Revert to default** to clear a single user's override, or **Revert all to default** to clear every override at once.
