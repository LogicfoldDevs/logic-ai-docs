---
title: Logs
description: System logs and error messages for diagnosing issues.
---

The Logs tab shows the **most recent 50 chat errors and warnings** from Logic AI. Use it to diagnose issues and understand what went wrong under the hood. (Routine informational events aren't surfaced here — this view is focused on problems.)

## Log Entries

Each entry shows a one-line summary; click it to expand. A row includes:

- **Severity** — Error or Warning
- **Timestamp** — When the event occurred
- **Source** — The Apex method that logged it
- **Message** — A human-readable description of what happened
- **HTTP status** — Shown when the event came from a gateway callout

Expanding an entry reveals full detail: the log name, method, the user and session it relates to, the full message, and a stack trace when one is available.

## Common Issues

| What you'll see | What it means |
|---|---|
| Callout failed | The connection to the AI gateway timed out or returned an error |
| Tool execution error | A tool (query, create, update) failed due to a Salesforce error (validation rule, required field, etc.) |
| HTTP 402 | The org is out of credits — top up from the [Credits](/products/logicai/docs/admin-credits) tab |
| HTTP 503 | The org's AI workspace is still being provisioned |
| Session limit reached | A conversation hit the maximum number of tool-use turns |

## Refreshing

Click **Refresh** to re-fetch the latest entries. There's no search box — the view always shows the most recent errors and warnings.

## Retention

Logs are stored in the `Bot_Log__c` custom object. Old logs can be deleted via Salesforce's standard data management tools or automated with a scheduled flow.
