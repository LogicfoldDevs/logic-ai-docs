---
title: Memory
description: Configure Logic AI's long-term memory — automatic capture, health tuning, and org knowledge.
---

The Memory tab manages Logic AI's long-term memory. Memory lets Logic AI remember facts about users and your org across conversations and get more useful over time.

Memory is **captured automatically**. As people chat, a background classifier distils durable facts into structured **memory items** and files them by scope (user, org, coworker, agent). Those items are then **recalled invisibly** — the relevant ones are injected into the prompt on the read path, with no "recall" tool and no loader step. Users don't manage memory by hand; they simply chat, and can steer it with 👍 / 👎 feedback (see [Feedback & Reactions](/products/logicai/docs/feedback-and-reactions)).

## Memory toggle

At the top of the tab, **Enable memory** turns the whole system on or off. When it's off, the memory layers are skipped in the prompt and the memory tools are hidden from the model.

## Memory health

A rolling **health score** (last 14 days) summarises how well memory is serving your users, based on the feedback signals it collects:

- **Happy** — a 👍 confirmed the recalled memory helped.
- **Missing** — the user indicated something should have been remembered but wasn't.
- **Too much** — the user indicated Logic AI recalled too much or the wrong thing.

Logic AI **auto-tunes capture** from these signals: the **aggressiveness** (how readily it captures new facts) and the **confidence floor** (the bar an item must clear to be kept) adjust themselves as feedback accrues. Click **Recompute** to apply the latest signals immediately.

## Rebuild from history

**Rebuild from history** scans every user's past chat sessions and messages and seeds structured memory from them. Any legacy (Version 1) memory is migrated in, then cleared once it's been folded into the new items. The rebuild is additive and de-duplicated, runs in the background, and uses credits for the analysis.

## Memory scopes

Memory items are grouped on the tab by scope:

- **Org context** — org-wide facts that apply to everyone (e.g. pipeline stages, what "Enterprise" means). You **review and curate** these here — see [Org memory review](#org-memory-review) below.
- **User context** — per-user facts, grouped by user and expandable. Read-only here (each user's items are private to that user; they curate their own from the chat via the [Your Memory](/products/logicai/docs/your-memory) panel).
- **Agent context** — items the agent has learned that help it operate. Read-only; the agent self-curates.

Coworker memory isn't shown here — it lives with each [coworker](/products/logicai/docs/coworkers) and is curated from the coworker's menu in the chat sidebar.

## Org memory review

Org-wide facts captured automatically don't go live immediately. Each one lands as **Pending review** and is held **out of everyone's prompts** until an admin acts on it, so shared memory stays deliberate. For each item you can:

- **👍 Approve** — start injecting it as a positive org fact.
- **👎 Approve as negative** — keep it injected, but framed as something Logic AI must *not* do or treat as true (useful for "we don't carry X").
- **✏️ Edit** — fix the wording; editing also approves it.
- **🗑 Delete** — remove it entirely.
- **↗ Move to…** — re-home the fact to a [coworker](/products/logicai/docs/coworkers) (or your own memory) instead of keeping it org-wide — handy when an auto-captured fact really belongs to one coworker's area of work.

You can also **add** an org fact yourself; anything an admin writes or edits is approved immediately. Approved items move to the **Reviewed** list, where the same actions stay available.

## Org schema knowledge (Deep Dive)

The **Run org deep dive scan** button scans every queryable object in your org — schema, relationships, record counts, and last activity — and asks the model to summarise what data your org holds and the workflows it supports. It produces two read-only blocks:

- **Data Structure** — a summary of your org's objects and relationships.
- **Workflow** — the workflows your data supports (this is what the `get_workflow` tool returns to the chat).

The scan pauses after the object sweep to show an **estimated credit cost** before the summarisation step runs, since the compress and synthesise callouts debit your gateway ledger. These blocks only refresh when you re-run the deep dive.

## Agent knowledge

Craft knowledge Logic AI accumulates automatically from recovering from recoverable tool errors — rule-level patterns (SOQL syntax, field-naming gotchas), not record-specific facts. It's read-only here; the agent self-curates it and a background consolidator dedupes it as it grows. You can **Consolidate now** to dedupe it or **Clear** it.

## Consolidation

Logic AI consolidates memory in the background as it grows or goes stale — merging near-duplicate facts, pruning stale items, and keeping the most useful information across the org and every user. You can trigger it manually with the **Consolidate now** buttons.
