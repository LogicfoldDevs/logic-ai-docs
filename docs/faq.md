---
title: FAQ
order: 4
---

# Frequently Asked Questions

## General

**What AI model does LogicAI use?**
LogicAI is powered by Anthropic's Claude. Your admin can configure which model is used from the admin console.

**Can LogicAI access data I don't have permission to see?**
No. All queries and operations run in your user context with full Salesforce sharing rules and field-level security enforced.

**Is my data sent to external servers?**
Conversation data is sent to Anthropic's API for processing. Your Salesforce data is not stored by Anthropic and is not used for model training. Each organization has its own isolated Anthropic workspace.

## Troubleshooting

**LogicAI says "being provisioned" when I try to chat**
Your organization's AI workspace is still being set up. This usually completes within a few minutes. If it persists, contact your Logicfold representative.

**I can't see the LogicAI component on record pages**
Ask your Salesforce admin to add the LogicAI component to the page layout using Lightning App Builder, and ensure you have the **Agentfold User** permission set assigned.

**LogicAI won't create or update records**
Write operations require streaming to be enabled. Ask your admin to check the Settings tab in the LogicAI admin console.

**I'm getting a "credit balance" error**
Your organization has used its allocated AI credits. Contact Logicfold to top up your balance.

## Security

**Where is my API token stored?**
The gateway token is stored in a Salesforce Named Credential using the External Credential framework. It is encrypted at rest and is not readable from Apex code — only usable for authorized callouts.

**Can I revoke access?**
Yes. An admin can disconnect from Logicfold at any time from the admin console. This immediately revokes the gateway token.
