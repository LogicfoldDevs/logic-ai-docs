---
title: Memory
description: Configure Logic AI's long-term memory for users, org knowledge, and agent learning.
---

The Memory tab manages Logic AI's long-term memory system. Memory lets Logic AI remember facts about users and your org, learn from past interactions, and get smarter over time.

## Memory Toggle

At the top of the tab, **Enable memory** turns the whole system on or off. When it's off, the memory layers are skipped in the prompt and the `remember_user` / `forget_user` / `remember_org` tools are hidden from the model.

## Memory Types

### Org Memory

Org-wide facts that apply to everyone, edited directly in a text box on this tab (one fact per line). Examples:

- "Pipeline stages: Discovery, POC, Negotiation, Closed Won/Lost"
- "'Enterprise' means accounts with ARR > $250K"
- "Account reviews happen quarterly"

You can type these in yourself, and the model can also append to them via the `remember_org` tool. Use **Clear** to wipe org memory.

### User Memory

Per-user facts and recent context that Logic AI remembers across conversations. Each user with memory has two editable sections:

- **Facts** — durable preferences, role, responsibilities, terminology, and recurring work
- **Recent items worked on** — short-term context like records, reports, or campaigns the user recently touched

Users can ask Logic AI to remember or forget things during conversation, and admins can edit, **Consolidate**, or **Delete** any user's memory from this tab. User memories are private to each user.

### Agent Knowledge

Craft lessons Logic AI learns automatically from recovering from recoverable tool errors — rule-level patterns (SOQL syntax, field-naming gotchas), not record-specific facts. It's read-only here; the agent self-curates it. You can **Consolidate now** to dedupe it or **Clear** it.

## Org Schema Knowledge (Deep Dive)

The **Run org deep dive scan** button scans every queryable object in your org — schema, relationships, record counts, and last activity — and asks the model to summarize what data your org holds and the workflows it supports. It produces two read-only blocks:

- **Data Structure** — a summary of your org's objects and relationships
- **Workflow** — the workflows your data supports (this is what the `get_workflow` tool returns to the chat)

The scan shows an estimated credit cost before the summarization step runs, since the compress and synthesize callouts debit your gateway ledger. These blocks only refresh when you re-run the deep dive.

## Memory Consolidation

When memory grows large (over 30KB for user memory, over 4KB for agent memory) or goes stale, Logic AI automatically consolidates it in the background — merging duplicates, removing outdated facts, and keeping the most useful information. You can also trigger consolidation manually with the **Consolidate now** buttons.
