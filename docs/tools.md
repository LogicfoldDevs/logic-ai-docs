---
title: Tools Reference
order: 11
---

# Tools Reference

LogicAI has a set of built-in tools that let it interact with your Salesforce data. Each tool can be individually enabled or disabled from the [Policies](/docs/admin-policies) tab.

## Query Tools

### soql_query
Run SOQL queries against any object the user has access to. LogicAI constructs the query based on the user's natural language request, executes it with `USER_MODE` sharing enforcement, and presents the results.

### describe_object
Inspect an object's fields, relationships, picklist values, and record types. LogicAI uses this automatically to understand your org's schema before building queries — you don't need to ask for it explicitly.

### get_record
Retrieve a single record by ID with specified fields. Useful when LogicAI needs to read the full details of a specific record it found via a query.

## Record Tools

### create_record
Create a new record on any standard or custom object. LogicAI will ask for confirmation before creating. Only available when streaming is enabled.

### update_record
Modify fields on an existing record. LogicAI shows what will change before applying. Only available when streaming is enabled.

### delete_record
Delete a record (sends it to the Recycle Bin — recoverable for 15 days). Disabled by default. Only available when streaming is enabled.

## Bulk Tools

### mass_create
Create multiple records in a single operation. Useful for requests like "Create 5 tasks for each of these contacts." Disabled by default — enable in Policies if your users need it.

### mass_update
Update multiple records at once. Useful for requests like "Set all these opportunities to Closed Lost." Disabled by default.

## Memory Tools

Available when memory is enabled in the [System](/docs/admin-system) tab:

### remember_user
Save a fact or preference about the current user. Persists across conversations. Example: a user says "Remember that I manage the West region" and LogicAI recalls this in future chats.

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
Records a lesson LogicAI learned from successful error recovery (e.g., "Field X requires value Y when Z is true"). Automatically managed — admins can view and clear agent memories from the [Memory](/docs/admin-memory) tab. Always enabled.

### get_workflow
Retrieve the admin-configured workflow instructions. Available when a workflow has been set in the System tab.

## Security Model

All tools run in the context of the current Salesforce user:

- **Sharing rules** are enforced — LogicAI cannot see records the user can't see
- **Field-level security** is enforced — restricted fields are invisible to LogicAI
- **Write operations** require streaming to be enabled (this prevents DML conflicts in non-streaming mode)
- **Admin tools** can only query admin-mode fields (like `Admin_Mode__c`) via `SYSTEM_MODE` — these are not exposed in normal chat
