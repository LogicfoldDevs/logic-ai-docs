---
title: FAQ
order: 12
---

# Frequently Asked Questions

## General

**What AI model does LogicAI use?**
LogicAI is powered by Anthropic's Claude. Your admin can configure which model is used from the [Settings](/docs/admin-settings) tab.

**Can LogicAI access data I don't have permission to see?**
No. All queries and operations run in your user context with full Salesforce sharing rules and field-level security enforced.

**Is my data sent to external servers?**
Conversation data is sent to Anthropic's API for processing. Your Salesforce data is not stored by Anthropic and is not used for model training. Each organization has its own isolated Anthropic workspace with a dedicated API key.

**How many tool steps can LogicAI take in one message?**
By default, up to 8 rounds of tool use per message. An admin can increase this from the [Settings](/docs/admin-settings) tab (up to 50 max, bounded by Salesforce governor limits).

**Does LogicAI work in Salesforce Classic?**
No. LogicAI requires Lightning Experience. The chat component is a Lightning Web Component (LWC) and is not available in Classic.

## Troubleshooting

**LogicAI says "being provisioned" when I try to chat**
Your organization's AI workspace is still being set up. This usually completes within a few minutes after connecting. If it persists, contact your Logicfold representative.

**I can't see the LogicAI component on record pages**
Two things to check:
1. Your admin needs to add the `logicAI` component to the page layout via Lightning App Builder
2. You need the **Agentfold User** permission set assigned to your user

**LogicAI won't create or update records**
Write operations (create, update, delete) require streaming to be enabled. Ask your admin to check the [Settings](/docs/admin-settings) tab. Also verify that the relevant tools are enabled in [Policies](/docs/admin-policies).

**I'm getting a "credit balance" error**
Your organization has used its allocated AI credits. An admin can purchase more from the [Credits](/docs/admin-credits) tab.

**LogicAI gives an error about "too many callouts"**
This happens when a complex request exceeds Salesforce's 100-callout-per-transaction limit. Try breaking your request into smaller steps, or reduce the Max Turns setting.

**The chat panel shows "temporarily unavailable"**
The admin has disabled the chatbot from the [Settings](/docs/admin-settings) tab. This is usually intentional (e.g., during maintenance).

## Security and Privacy

**Where is my API token stored?**
The gateway token is stored in a Salesforce Named Credential using the External Credential framework. It is encrypted at rest and is not readable from Apex code — only usable for authorized callouts.

**Can I revoke access?**
Yes. An admin can disconnect from Logicfold at any time from the [Settings](/docs/admin-settings) tab. This immediately revokes the gateway token and stops all AI conversations.

**Is there an audit trail?**
Yes. All record modifications made through LogicAI are logged in the [Audit](/docs/admin-audit) tab with full traceability — who requested it, what changed, and when.

**Does Logicfold have access to my Salesforce data?**
No. Logicfold's gateway proxies requests to Anthropic but does not store conversation content. The gateway tracks usage (token counts, credit balances) but not the content of your queries or data.
