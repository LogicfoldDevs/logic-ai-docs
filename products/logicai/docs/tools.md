---
title: Tools Reference
description: Complete list of tools Logic AI can use to interact with your Salesforce data.
---

Logic AI has a set of built-in tools that let it interact with your Salesforce data. Each tool can be individually enabled or disabled — org-wide or per user — from the [Policies](/docs/admin-policies) tab.

## Query Tools

### soql_query
Run SOQL queries against any object the user has access to. Logic AI constructs the query based on the user's natural language request, executes it with `USER_MODE` sharing enforcement, and presents the results. The maximum number of rows returned per call is configurable in Policies (default 50). **Enabled by default.**

### get_record
Retrieve a single record by ID with specified fields. Useful when Logic AI needs to read the full details of a specific record it found via a query. **Enabled by default.**

### describe_object
Inspect an object's fields, relationships, picklist values, and record types. Logic AI uses this automatically to understand your org's schema before building queries — you don't need to ask for it explicitly. **Enabled by default.**

## Record Tools

### create_record
Create a new record on any standard or custom object. Disabled by default. Logic AI asks for confirmation before creating (configurable in Policies).

### update_record
Modify fields on an existing record. Disabled by default. Logic AI shows what will change before applying (configurable in Policies).

### delete_record
Delete a record (sends it to the Recycle Bin — recoverable for 15 days). Disabled by default. Deletes **always** require in-chat approval — this cannot be turned off.

## Bulk Tools

### mass_create_records
Create multiple records in a single operation. Useful for requests like "Create 5 tasks for each of these contacts." Disabled by default. The per-call record cap is configurable in Policies (default 200).

### mass_update_records
Update multiple records at once. Useful for requests like "Set all these opportunities to Closed Lost." Disabled by default. Per-call cap configurable (default 200).

### mass_delete_records
Delete multiple records at once. Disabled by default and **locked** — reach out to Logicfold to enable it for your org. Like single deletes, it always requires in-chat approval.

## File Tools

### generate_csv
Build a CSV file from query results and attach it to the chat session for download. Disabled by default.

### generate_pdf
Compose a rich, formatted report in the side panel that can be exported. Disabled by default.

## Memory Tools

Available when memory is enabled on the [Memory](/docs/admin-memory) tab:

### remember_user
Save a fact or preference about the current user. Persists across conversations. Example: a user says "Remember that I manage the West region" and Logic AI recalls this in future chats.

### forget_user
Remove a previously saved user memory.

### remember_recent_item
Bookmark a record or piece of data the user was recently working with.

### forget_recent_item
Remove a bookmarked recent item.

### remember_org
Save org-wide knowledge that benefits all users. Example: "Remember that our fiscal year starts in April."

## Utility Tools

### get_tool_result
Re-read the output of a previous tool call in the same session. Used internally when older tool results have been compacted from the conversation to save tokens. Always enabled.

### remember_agent
Records a lesson Logic AI learned from successful error recovery (e.g., "Field X requires value Y when Z is true"). Automatically managed — admins can view and clear agent memories from the [Memory](/docs/admin-memory) tab. Always enabled.

### get_workflow
Retrieve the org's workflow/SOP knowledge. This becomes available once the **org deep dive** has been run from the [Memory](/docs/admin-memory) tab, which generates a summary of your org's data structure and workflows.

## Security Model

All tools run in the context of the current Salesforce user:

- **Sharing rules** are enforced — Logic AI cannot see records the user can't see
- **Field-level security** is enforced — restricted fields are invisible to Logic AI
- **Write operations** (create, update, delete, and the bulk/file tools) run on the streaming path, which keeps DML from conflicting with the agent's callout loop
- **Admin tools** can only query admin-mode fields (like `Admin_Mode__c`) via `SYSTEM_MODE` — these are not exposed in normal chat
