---
title: Coworkers
description: Create focused chat personas — each with its own memory, instructions, and sharing — in the Logic AI sidebar.
---

**Coworkers** are focused chat personas you create in the Logic AI sidebar. Each coworker is a named assistant with its own memory, its own colour, optional standing instructions, and its own set of chats — so you can keep a "Renewals" coworker separate from a "Data cleanup" coworker instead of running everything through one general chat.

A coworker isn't a different AI — it's the same Logic AI, scoped to a job. It runs in **your** user context with all the same permissions, tools, and approvals as any other chat.

## Why use coworkers

- **Separate contexts** — keep unrelated work in its own lane. A coworker only ever sees the chats and memory that belong to it.
- **Standing instructions** — give a coworker a persistent role once ("You help me manage EMEA renewals; always check the contract end date first") instead of repeating it every conversation.
- **Its own memory** — each coworker remembers facts relevant to its job, and nothing bleeds between coworkers or into your general chat.
- **Shareable** — make a coworker available to specific teammates or your whole org, so everyone works from the same persona and shared memory.

## Creating a coworker

In the chat sidebar, click **+ New coworker** and fill in:

- **Name** — what it does, e.g. *Renewals*, *Support triage*, *Data cleanup* (required, up to 80 characters).
- **Instructions** *(optional)* — standing guidance applied to every chat with this coworker. Think of it as a mini system prompt for this persona.
- **Colour** — a swatch so you can spot the coworker at a glance. Leave it and Logic AI auto-assigns a distinct colour from the palette.
- **Visibility** — who can use it (see below).

Your coworkers appear as chips in the sidebar. Click one to start (or continue) a chat with it; its colour tags the chats that belong to it.

> Your admin can restrict this. If **Disable creating coworkers** is on you won't see **+ New coworker** (you can still use coworkers shared with you), and if **Coworkers only** is on the general **New chat** is hidden so you work entirely through coworkers. See [Policies](/products/logicai/docs/admin-policies#chat--coworkers).

## Visibility &amp; sharing

Every coworker has one of three visibility settings:

| Visibility | Who can use it |
|---|---|
| **Private** | Only you (the owner). This is the default. |
| **Specific users** | You, plus the teammates you pick. |
| **Org** | Everyone in your org who has Logic AI. |

Notes on how sharing works:

- When you choose **Specific users**, a search box lets you add teammates. Only users who actually have Logic AI assigned (one of the Logic AI permission sets) appear in the search.
- **Only the owner** can rename, recolour, re-share, or delete a coworker.
- A shared coworker shares its **memory** with everyone who can use it — that's the point, so the team works from the same context. But **chats are private to each user**: even on a shared coworker, you only see your own conversations, and the "3 chats" count next to a coworker reflects *your* chats with it.

## Coworker memory

Each coworker keeps its own memory, separate from your personal memory and from other coworkers. It's captured the same way the rest of Logic AI's memory works — automatically, as you chat — and recalled invisibly in future conversations with that coworker. See [Memory](/products/logicai/docs/admin-memory) for how capture and recall work.

You can review a coworker's memory from its menu in the sidebar:

- **View** the facts it has learned.
- **Edit** a fact to correct it.
- **Forget** a fact you don't want it to keep (it's tombstoned so the capture layer won't silently re-learn it).
- **Move** a fact to your own memory, to org memory, or to another coworker you can use — useful when a fact ends up on the wrong coworker or really belongs org-wide.

Because a shared coworker's memory is shared, **anyone who can use the coworker can curate its memory** — a small, collaborative shared brain for the team.

Owners can also regenerate a coworker's **guidelines** — a short, model-written summary of how the coworker should work, distilled from its memory. Guidelines refresh automatically after memory consolidation; the owner can trigger a refresh manually from the coworker's menu.

## Deleting a coworker

Deleting a coworker (owner only) removes the coworker and **purges its memory**. Your existing chats aren't deleted — they're simply unlinked from the coworker and fall back into your general **recent chats** list.
