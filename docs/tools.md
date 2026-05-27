---
title: Tools
order: 3
---

# Tools

LogicAI comes with a set of built-in tools that let it interact with your Salesforce data. Each tool can be enabled or disabled per policy.

## Query Tools

- **soql_query** — Run SOQL queries to read data from any object the user has access to. All queries respect Salesforce sharing rules and field-level security.
- **describe_object** — Inspect an object's fields, relationships, and picklist values. Used by LogicAI to understand your org's schema before querying.

## Record Tools

- **get_record** — Retrieve a single record by ID with specified fields.
- **create_record** — Create a new record on any standard or custom object.
- **update_record** — Update fields on an existing record.
- **delete_record** — Delete a record (moves to Recycle Bin).

## Bulk Tools

- **mass_create** — Create multiple records in a single operation.
- **mass_update** — Update multiple records at once.

## Memory Tools

When memory is enabled in settings:

- **remember_user** — Save a fact or preference about the current user for future conversations.
- **forget_user** — Remove a previously saved user memory.
- **remember_org** — Save org-wide knowledge that benefits all users.

## Tool Security

All tools run in the context of the current user. LogicAI cannot access data the user doesn't have permission to see. Write operations (create, update, delete) are only available when streaming is enabled.
