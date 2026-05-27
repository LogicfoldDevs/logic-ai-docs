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

Click **Buy Credits** to open a Stripe checkout session. Credit packs are available in several tiers. After a successful purchase, credits are added to your balance immediately.
