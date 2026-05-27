---
title: Audit
description: View the full event log of actions taken through LogicAI.
---

The Audit tab provides a complete event log of significant actions taken through LogicAI.

## What Gets Audited

- **Record creation** — Every record created by Logic AI, including the object type, record ID, and which user requested it
- **Record updates** — Field changes made through Logic AI, with before/after values
- **Record deletions** — Records sent to the Recycle Bin via Logic AI
- **Bulk operations** — Mass creates and updates with record counts
- **Policy changes** — When an admin modifies tool policies or user roles
- **Connection events** — Gateway connect/disconnect actions

## Filtering

Use the filters at the top of the Audit tab to narrow results by:

- **User** — See actions from a specific user
- **Date range** — Filter to a specific time period
- **Action type** — Show only creates, updates, deletes, etc.

## Why It Matters

The audit log gives you full traceability for compliance and troubleshooting. If a user reports that Logic AI modified the wrong record, you can trace exactly what happened, when, and who requested it.

All audit records are stored in the `Bot_Audit__c` custom object and are subject to your org's data retention policies.
