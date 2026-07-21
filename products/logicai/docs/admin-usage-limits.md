---
title: Usage Limits
description: Track monthly spend and cap it per source and per user, in USD.
---

Usage Limits let you see where your AI spend is going and cap it — per **source** and per **user** — in USD per calendar month. Spend, limits, and caps all reset on the 1st.

These controls live on the **Usage** tab in the admin console (they moved out of the [Credits](/products/logicai/docs/admin-credits) tab).

## By source

Every place Logic AI is called from is a **source** — the chat itself, plus any integration that calls the [global Apex API](/products/logicai/docs/developer/overview). Each source row shows its **model**, **spend so far this month**, its **limit**, and whether it's **enabled**.

Click **Edit** on a row to:

- **Set a monthly limit** — choose **No cap** or **Amount** and enter a USD figure. When a source reaches its limit, its calls are refused until the next month (or until you raise it).
- **Change the model** the source runs on.
- **Enable or disable** the source — a disabled source's calls are rejected, a quick way to switch off one integration without touching code.

Chat and internal/background callers are grouped together as a single **chat** bucket; each integration registered through the API appears as its own row (named by the source key the developer chose — see [Source Registration](/products/logicai/docs/developer/registration)).

## By user

Spend per user, with a monthly **Cap** you can set per person (**No cap** or an **Amount**). A user with no cap of their own falls back to the **org default** user cap. When a user reaches their cap, their calls are refused until the next month.

## How limits are enforced

Caps are enforced **in addition to** your organization's overall credit balance — a call is refused if it would exceed *either* an applicable cap *or* the remaining balance. Buying more [credits](/products/logicai/docs/admin-credits) does not lift a cap, and raising a cap does not add credits; they're independent controls.

When a call is refused for either reason, users see a friendly "out of credits" message in chat, and integrations calling the API get a `402` response — see [Errors & Status Codes](/products/logicai/docs/developer/errors).
