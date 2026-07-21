---
title: Credits
description: Manage your AI credit balance and purchase more credits.
---

The Credits tab manages your organization's AI credit balance. Every Logic AI conversation consumes credits based on the AI model used and the length of the conversation.

## How Credits Work

- Each API call to the AI model costs credits based on token usage (input + output)
- More capable models cost more credits per token
- Tool-use conversations (where Logic AI runs queries, creates records, etc.) use more credits because they involve multiple AI round-trips
- When your balance hits zero, users see a friendly "out of credits" message and cannot start new conversations

## Checking Your Balance

The current credit balance is displayed at the top of the Credits tab and also on the Dashboard.

## Purchasing Credits

Choose one of the preset credit packs or enter a custom amount, then check out. Payment is processed securely by Stripe. After a successful purchase, credits are added to your balance immediately and you're returned to the Credits tab.

## Saved Card

You can save a payment method to make future top-ups one click — the saved card sits next to your balance. Add a card at any time, and remove it whenever you like. Saving a card is also what enables **auto-replenish** (below).

## Auto-Replenish

Turn on auto-replenish to keep your balance from ever hitting zero mid-conversation. Set a **threshold** (top up when the balance drops below this) and an **amount** (how many credits to add), and Logic AI charges your saved card automatically in the background whenever the balance falls below the threshold. Auto-replenish requires a saved card; turning it off clears the threshold and amount so nothing fires unexpectedly.

## Transaction History

The Credits tab lists your purchases and top-ups, grouped by day. You can:

- **Filter by type** to narrow the list
- **Download CSV** to export the history (works inside orgs with Lightning Web Security enabled)
- **Request receipt** on any transaction to have a receipt emailed to you

## This Month's Spend

Your USD spend for the current month, and the **per-source** and **per-user** spend caps, now live on their own [Usage](/products/logicai/docs/admin-usage-limits) tab in the admin console.
