---
title: Audit
description: View the full event log of actions taken through Logic AI.
---

The Audit tab logs every **DML tool call** Logic AI ran on your org — the create, update, and delete operations.

## What Gets Audited

- **Record creation** — Every record created by Logic AI, including the object type, record ID, and which user requested it
- **Record updates** — Field changes made through Logic AI
- **Record deletions** — Records sent to the Recycle Bin via Logic AI
- **Bulk operations** — Mass creates, updates, and deletes with record counts

Each row expands to show the user prompt that triggered it, the field changes (or record IDs), the raw tool input, and any error. Read-only reads (queries, describes) are not audited here — see the [Logs](/products/logicai/docs/admin-logs) tab for those.

## Filtering

Use the filters at the top of the Audit tab to narrow results by:

- **User** — See actions from a specific user
- **Date range** — Filter to a **From** and **To** date

Use **Clear filters** to reset.

## Why It Matters

The audit log gives you full traceability for compliance and troubleshooting. If a user reports that Logic AI modified the wrong record, you can trace exactly what happened, when, and who requested it.

All audit records are stored in the `Bot_Audit__c` custom object and are subject to your org's data retention policies.
