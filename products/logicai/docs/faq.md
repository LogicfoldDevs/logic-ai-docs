---
title: FAQ
description: Common questions about Logic AI, troubleshooting, and security.
---

## General

**What AI model does Logic AI use?**
Logic AI is powered by Anthropic's Claude. Your admin can configure which model is used from the [Settings](/products/logicai/docs/admin-settings) tab.

**Can Logic AI access data I don't have permission to see?**
No. All queries and operations run in your user context with full Salesforce sharing rules and field-level security enforced.

**Is my data sent to external servers?**
Conversation data is sent to Anthropic's API for processing. Your Salesforce data is not stored by Anthropic and is not used for model training.

**Does Logic AI work in Salesforce Classic?**
No. Logic AI requires Lightning Experience. The chat component is a Lightning Web Component (LWC) and is not available in Classic.

**Can I call Logic AI from Apex, Flows, or triggers?**
Yes. Logic AI ships a global Apex API (`lai.LogicAI`) so your own automation can send a prompt and get a reply, using the same gateway and credits as the chat. Register a source once, then call `invoke` (synchronous) or `invokeAsync` (for Flows/triggers). See the [Developer](/products/logicai/docs/developer/overview) section, and note that admins can keep each integration in budget with per-source [usage limits](/products/logicai/docs/admin-usage-limits).

## Troubleshooting

**Logic AI says "being provisioned" when I try to chat**
Your organization's AI workspace is still being set up. This usually completes within a few minutes after connecting. If it persists, contact your Logicfold representative.

**I can't see the LogicAI component on record pages**
Two things to check:
1. Your admin needs to add the Logic AI component to the page layout via Lightning App Builder
2. You need the correct permission set assigned to your user

**Logic AI won't create or update records**
Write tools (create, update, delete, and the bulk/file tools) are **disabled by default**. Ask your admin to enable the ones you need on the [Policies](/products/logicai/docs/admin-policies) tab. Note that delete operations always require in-chat approval, and mass delete is locked until Logicfold enables it for your org.

**I'm getting a "credit balance" error**
Your organization has used its allocated AI credits. An admin can purchase more from the [Credits](/products/logicai/docs/admin-credits) tab.

**Logic AI gives an error about "too many callouts"**
This happens when a complex request exceeds Salesforce's 100-callout-per-transaction limit. Try breaking your request into smaller steps.

**The chat panel shows "temporarily unavailable"**
The admin has disabled the chatbot from the [Settings](/products/logicai/docs/admin-settings) tab. This is usually intentional (e.g., during maintenance).

## Security and Privacy

**Where is my API token stored?**
The gateway token is stored in a Salesforce Named Credential using the External Credential framework. It is encrypted at rest and is not readable from Apex code — only usable for authorized callouts.

**Can I revoke access?**
Yes. An admin can disconnect from Logicfold at any time from the [Settings](/products/logicai/docs/admin-settings) tab. This immediately revokes the gateway token and stops all AI conversations.

**Is there an audit trail?**
Yes. All record modifications made through LogicAI are logged in the [Audit](/products/logicai/docs/admin-audit) tab with full traceability — who requested it, what changed, and when.

**Does Logicfold have access to my Salesforce data?**
No. Logicfold's gateway proxies requests to Anthropic but does not store conversation content. The gateway tracks usage (token counts, credit balances) but not the content of your queries or data.
