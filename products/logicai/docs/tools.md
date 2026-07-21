---
title: Tools Reference
description: Complete list of tools Logic AI can use to interact with your Salesforce data.
---

Logic AI has a set of built-in tools that let it interact with your Salesforce data. Each tool can be individually enabled or disabled — org-wide or per user — from the [Policies](/products/logicai/docs/admin-policies) tab.

## Query Tools

### soql_query
Run SOQL queries against any object the user has access to. Logic AI constructs the query based on the user's natural language request, executes it with `USER_MODE` sharing enforcement, and presents the results. The maximum number of rows returned per call is configurable in Policies (default 50). **Enabled by default.**

### get_record
Retrieve a single record by ID with specified fields. Useful when Logic AI needs to read the full details of a specific record it found via a query. **Enabled by default.**

### describe_object
Inspect an object's fields, relationships, picklist values, and record types. Logic AI uses this automatically to understand your org's schema before building queries — you don't need to ask for it explicitly. **Enabled by default.**

### sosl_search
Search for a term across multiple objects at once (a SOSL search), useful when you don't know which object a record lives on — e.g. "find anything mentioning Acme." **Enabled by default.**

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

## Action Tools

These let Logic AI take action in your org beyond reading and writing records. **All are enabled by default** and can be turned off per tool on the [Policies](/products/logicai/docs/admin-policies) tab. Each can optionally require in-chat approval before it runs.

### send_email
Send an email on the user's behalf. Enabled by default, and **requires in-chat approval by default** — Logic AI shows the recipients, subject, and body before anything is sent.

### send_notification
Send a Salesforce custom notification to users (the bell-icon notifications in Lightning). **Enabled by default.**

### post_to_chatter
Post a Chatter update to a record's feed or a group. **Enabled by default.**

### run_report
Run an existing Salesforce report and return its results. **Enabled by default.**

### create_report
Build a new Salesforce report definition. **Enabled by default.**

### invoke_apex_action
Call an invocable Apex action exposed in your org. **Enabled by default.**

### invoke_flow
Launch an autolaunched Flow. **Enabled by default.**

## File Tools

### generate_csv
Build a CSV file from query results and attach it to the chat session for download. CSV exports include the full result set (they are not limited by the SOQL row cap). Disabled by default.

### generate_pdf
Compose a rich, formatted report in the side panel that can be exported. Disabled by default.

### read_file
Read the files attached to or related to a record — PDFs, images, text, and other file types — and return them as content Logic AI can actually see, so it can summarize or answer questions about an attachment. Always enabled (a safe, read-only capability with no side effects, so it isn't listed on the Policies tab).

## Metadata Tools

Read-only tools that let Logic AI look up how your org is built — Apex classes, Flows, validation and workflow rules, permission sets, and LWC/Aura components — via the Tooling API, to answer questions like "what does this validation rule do?" **Admins only:** these run only for users with the Logic AI **Admin** permission set, and reading Apex additionally requires the running user's own "Author Apex" permission. Enabled by default; they appear in a **Metadata (Admins only)** group on the [Policies](/products/logicai/docs/admin-policies) tab.

### list_metadata
List metadata components of a given type (e.g. Apex classes, Flows, validation rules) so Logic AI can find the right one to read. **Enabled by default (admins only).**

### read_metadata
Read a specific component's definition as structured detail — e.g. the body of an Apex class or the logic of a Flow or validation rule. **Enabled by default (admins only).**

## Scheduled Agent Tools

These let Logic AI set up and manage [Scheduled Agents](/products/logicai/docs/scheduled-agents) — saved tasks that run on their own — right from a chat. They're available when Scheduled Agents is enabled (on by default; toggled per org or per user on the [Policies](/products/logicai/docs/admin-policies) tab).

### agent_creator
Create a scheduled agent from a plain-English description, e.g. "Every Monday at 8am, email me a summary of new leads." Logic AI captures the goal, schedule, and the tools the agent may use, then saves it to the **Scheduled Agents** tab.

### agent_editor
Update an agent the user already created — its instructions, schedule, tools, model, max turns, name, or whether it's active. Tool changes are checked against the tools agents are allowed to use, and Logic AI names any tool that needs admin approval.

## Memory Tools

Logic AI's long-term memory is captured automatically and recalled invisibly (there is no "recall" tool) — see [Memory](/products/logicai/docs/admin-memory). The tools below let the model **write** to memory during a chat, and are available when memory is enabled:

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

### ask_user_question
Pause and present a clickable multiple-choice prompt in the chat when Logic AI needs you to choose between options before continuing — instead of making you type the answer. Always enabled.

### remember_agent
Records a lesson Logic AI learned from successful error recovery (e.g., "Field X requires value Y when Z is true"). Automatically managed — admins can view and clear agent memories from the [Memory](/products/logicai/docs/admin-memory) tab. Always enabled.

### get_workflow
Retrieve the org's workflow/SOP knowledge. This becomes available once the **org deep dive** has been run from the [Memory](/products/logicai/docs/admin-memory) tab, which generates a summary of your org's data structure and workflows.

## Security Model

All tools run in the context of the current Salesforce user:

- **Sharing rules** are enforced — Logic AI cannot see records the user can't see
- **Field-level security** is enforced — restricted fields are invisible to Logic AI
- **Write operations** (create, update, delete, and the bulk/file tools) run on the streaming path, which keeps DML from conflicting with the agent's callout loop
- **Admin tools** can only query admin-mode fields (like `Admin_Mode__c`) via `SYSTEM_MODE` — these are not exposed in normal chat
