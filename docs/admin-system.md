---
title: System
description: Customize the system prompt, starter suggestions, and memory settings.
---

The System tab controls LogicAI's behavior at the deepest level — the system prompt and the starter suggestions users see when they open a new chat.

## System Prompt

The system prompt is the instruction set that shapes how LogicAI behaves in your org. It tells the AI:

- What its role is (e.g., "You are a helpful Salesforce assistant for Acme Corp")
- How to respond (tone, format, level of detail)
- What domain knowledge to apply
- Any org-specific rules or constraints

LogicAI ships with a carefully tuned default system prompt. You can customize it from this tab to tailor the AI's personality and knowledge to your organization.

### Tips for Customizing

- **Be specific** — "You help our sales team manage pipeline" works better than "Be helpful"
- **Add domain context** — If your org uses custom terminology, define it here
- **Set boundaries** — If certain objects or actions should be off-limits, state it explicitly
- **Keep it concise** — The system prompt is sent with every API call; longer prompts cost more credits

## Starter Suggestions

Starter suggestions are the example prompts shown to users when they open a new chat session. They help users understand what LogicAI can do and encourage adoption.

You can customize these to match your org's use cases. Good starter suggestions are:

- Specific to your business ("Show me overdue invoices from this month")
- Actionable ("Create a follow-up task for this contact")
- Varied (mix queries, record operations, and analysis)

## Memory Toggle

The System tab also includes the master toggle for memory features. When disabled, LogicAI will not store or recall any user or org memories. Agent memory consolidation is also paused.
