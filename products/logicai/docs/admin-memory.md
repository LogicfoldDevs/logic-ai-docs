---
title: Memory
description: Logic AI's long-term memory — fully automatic, with optional admin control over company knowledge.
---

Memory lets Logic AI remember facts about your users and your org across conversations and get more useful over time. **It runs entirely on its own** — nobody needs to review, approve or rebuild anything. This tab is an optional safety valve: use it to turn memory on or off, and to look at or correct what Logic AI has learned about your company.

## How it works

- **Capture** — after each message, a background step saves durable facts (preferences, terminology, how work is done, where data lives, corrections). After each chat, a second pass learns **habits** (applied once seen in two separate chats), **unfinished work**, and **repeated tasks** worth automating.
- **Recall** — every message gets the user's profile plus anything relevant to what they just asked and the record they have open, with no tool call or loader. See [Your Memory](/products/logicai/docs/your-memory) for what users experience.
- **Upkeep** — every night Logic AI tidies memory on its own: it indexes older facts for search, expires stale and finished items, fades habits that stopped showing up, merges duplicates, and learns from the past chats of anyone it hasn't learned from yet. This is scheduled automatically when the package is installed; on a quiet day it does almost nothing and uses almost no credits.
- **Forgetting** — users say *"forget …"* in chat. A forgotten fact is never re-learned, even reworded.

Memory is designed not to raise chat costs: the part of each message that changes from question to question is attached to that message, so the rest of the conversation stays cached.

## Memory toggle

**Enable memory** turns the whole system on or off (it's on by default). When it's off, Logic AI stops learning and stops using what it has learned.

## Org memory

Company-wide facts that apply to everyone (e.g. pipeline stages, what "Enterprise" means). There is **no approval step**: an automatically learned fact is used once Logic AI is confident about it or has heard it in two separate chats. Facts that haven't reached that bar yet are marked **Still learning** and aren't used.

You can:

- **Add** a fact yourself — admin-written facts are used immediately.
- **Edit** a fact to fix its wording.
- **Delete** a fact — it stops being used and won't be learned again.

When a chat user says an org fact is wrong, Logic AI stops using it until it's confirmed again; only an admin can delete it outright.

## User and agent context

- **User context** — per-user facts, grouped by user and expandable. Read-only here; each user's memory is private to them and managed by simply chatting.
- **Agent context** — items the agent has learned that help it operate. Read-only; the agent self-curates.

Coworker memory isn't shown here — it lives with each [coworker](/products/logicai/docs/coworkers).

## Org schema knowledge (Deep Dive)

The **Run org deep dive scan** button scans every queryable object in your org — schema, relationships, record counts, and last activity — and asks the model to summarise what data your org holds and the workflows it supports. It produces two read-only blocks:

- **Data Structure** — a summary of your org's objects and relationships.
- **Workflow** — the workflows your data supports (this is what the `get_workflow` tool returns to the chat).

The scan pauses after the object sweep to show an **estimated credit cost** before the summarisation step runs, since the compress and synthesise callouts debit your gateway ledger. These blocks only refresh when you re-run the deep dive.

## Agent knowledge

Craft knowledge Logic AI accumulates automatically from recovering from recoverable tool errors — rule-level patterns (SOQL syntax, field-naming gotchas), not record-specific facts. It's read-only here; the agent self-curates it and a background consolidator dedupes it as it grows. You can **Consolidate now** to dedupe it or **Clear** it.
