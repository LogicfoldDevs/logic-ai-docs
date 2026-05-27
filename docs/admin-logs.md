---
title: Logs
description: System logs and error messages for diagnosing issues.
---

The Logs tab shows system-level logs and errors from LogicAI. Use this tab to diagnose issues, monitor health, and understand what's happening under the hood.

## Log Entries

Each log entry includes:

- **Timestamp** — When the event occurred
- **Level** — INFO, WARN, or ERROR
- **Message** — A human-readable description of what happened
- **Details** — Expandable section with full context (request/response data, stack traces, etc.)

## Common Log Messages

| Message | What it means |
|---|---|
| Credit balance low | Your org is running low on credits — top up soon |
| Callout failed | The connection to the AI gateway timed out or returned an error |
| Tool execution error | A tool (query, create, update) failed due to a Salesforce error (validation rule, required field, etc.) |
| Memory consolidation triggered | Background memory cleanup started |
| Session limit reached | A conversation hit the maximum number of tool-use turns |

## Searching Logs

Use the search bar to filter logs by keyword. Common searches:

- `ERROR` — Show only errors
- A specific user name — See logs related to that user's sessions
- An object name — Find tool errors related to a specific Salesforce object

## Retention

Logs are stored in the `Bot_Log__c` custom object. Old logs can be deleted via Salesforce's standard data management tools or automated with a scheduled flow.
