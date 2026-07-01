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

Choose one of the preset credit packs or enter a custom amount, then check out. Payment is processed securely by Stripe. After a successful purchase, credits are added to your balance immediately.

## This Month's Spend

Below the balance, the **This month's spend** section shows USD spend so far this calendar month. Limits and caps reset on the 1st. It breaks spend down two ways:

### By source

Every place Logic AI is called from is a **source** — the chat itself, plus any integration that calls the [global Apex API](/products/logicai/docs/developer/overview). Each source shows its **model**, **spend so far**, its **limit**, and whether it's **enabled**. Click **Edit** on a row to:

- **Set a monthly limit** — choose **No cap** or **Amount** and enter a USD figure. When a source reaches its limit, its calls are refused until the next month (or until you raise it).
- **Change the model** the source runs on.
- **Enable or disable** the source — a disabled source's calls are rejected, a quick way to switch off one integration.

Chat and internal/background callers are grouped together as one "chat" bucket; each integration you registered via the API appears as its own row.

### By user

Spend per user, with a monthly **Cap** you can set per person (**No cap** or an **Amount**). A user who has no cap of their own falls back to the org default user cap. When a user reaches their cap, their calls are refused until the next month.

> Spend caps are enforced **in addition to** your overall credit balance — a call is refused if it would exceed *either* an applicable cap or the remaining balance. Developers calling the API get a `402` response in that case; see [Errors & Status Codes](/products/logicai/docs/developer/errors).
