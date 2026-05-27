---
title: "Admin: Memory"
order: 6
---

# Memory

The Memory tab manages LogicAI's long-term memory system. Memory allows LogicAI to remember facts about users, learn from past interactions, and get smarter over time.

## Memory Types

### User Memory

Per-user facts and preferences that LogicAI remembers across conversations. Examples:

- "This user prefers results in table format"
- "This user works primarily with the West region accounts"
- "This user's timezone is Pacific"

Users can ask LogicAI to remember or forget things during conversation. User memories are private to each user.

### Org Memory

Org-wide knowledge that benefits all users. Examples:

- "The fiscal year starts in April"
- "The 'Priority' field on Cases uses values: P1, P2, P3, P4"
- "Opportunities over $100K require VP approval"

Any user can ask LogicAI to remember something for the org.

### Agent Memory

Lessons that LogicAI learns automatically from successful error recovery during conversations. For example, if LogicAI encounters a field validation rule and figures out how to work around it, it remembers that pattern for future conversations with all users.

Agent memory is self-curating — LogicAI consolidates and deduplicates it automatically.

## Memory Consolidation

When memory grows large (over 30KB for user memory, over 4KB for agent memory), LogicAI automatically consolidates it — merging duplicates, removing outdated facts, and keeping the most useful information. This runs in the background and doesn't affect active conversations.

## Managing Memory

From the Memory tab you can:

- **View** all stored memories (user, org, and agent)
- **Delete** individual memories or clear all memories for a user
- **Trigger consolidation** manually if needed
- **Enable/disable** memory features from the System tab
