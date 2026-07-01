---
title: Source Registration & Spend Caps
description: Register a source before calling the API, and control spend with monthly USD caps.
---

Every call to the global API is attributed to a **source** — a named caller you register once. The source is what supplies the AI **model**, the **attribution key** (so its usage shows up separately in reporting), and its **monthly spend limit**. Registration is mandatory: the API will not run for an unregistered source.

## Registering a source

Call `register` once, at setup, and store the returned **registration id**:

```apex
Id regId = lai.LogicAI.register('NightlySync', 'claude-sonnet-4-6');
// Persist regId (e.g. in Custom Metadata or a Custom Setting) and reuse it.
```

- **Idempotent** — calling `register('NightlySync', ...)` again returns the **same** id. It won't create duplicates.
- **Don't register on every invoke.** Register once, keep the id, and pass it on each `Request.registrationId`.
- **Model** — must be a catalogued gateway model, or blank to use the org default. An unknown model is rejected at register time so you find out immediately, not at call time.
- Re-registering with a new model **updates** the source's model; re-registering with a blank model leaves an admin-set model untouched. Registration never changes the admin-managed spend limit or the enabled flag.

Behind the scenes a source is a **Logic AI Source** record (`Bot_Source__c`), keyed on your source string. The registration id is that record's Id.

> **Breaking change (v1.63):** `registrationId` is now **required** on every `invoke` / `invokeAsync` call, and there is no fallback for unregistered callers. If you used the API before this release, add a one-time `register(...)` and pass the id it returns.

## Choosing a source name

Pick a stable, descriptive name per logical caller — e.g. `NightlySync`, `CaseClassifier`, `QuoteDrafter`. Usage, spend, and the spend limit are all tracked per source, so a good name is one you'll want to see on the admin **Credits** tab. Reuse the same name (and id) for all calls from that integration.

## Monthly spend caps

Admins can cap spend in **USD per calendar month** at three levels. Caps and limits reset on the 1st. All of this is managed on the [Credits](/products/logicai/docs/admin-credits) tab — no code required.

| Level | What it limits | Where it's set |
|---|---|---|
| **Per source** | A single registered source's monthly spend | Credits tab → **By source** → set a **Limit** on the source |
| **Per user** | An individual user's monthly spend across everything | Credits tab → **By user** → set a **Cap** on the user |
| **Org default (per user)** | The default cap applied to users without their own | Credits tab → default user cap |

When a call would exceed an applicable cap, the gateway refuses it and the response comes back with a credit/limit error (see [Errors &amp; Status Codes](/products/logicai/docs/developer/errors)). Caps are enforced **in addition to** the org's overall credit balance — running out of either stops calls.

### The credit multiplier vs. spend caps

`Request.creditMultiplier` (1–100) marks **up the credits debited** for a call without changing the underlying AI cost — useful if you resell or internally charge back Logic AI usage. Because caps are measured in the resulting spend, a higher multiplier reaches a cap sooner. Leave it unset (1) for straight pass-through billing.

## Disabling a source

A source can be **disabled** from the Credits tab. A disabled source's calls are rejected (its `invoke` returns an error and `invokeAsync` throws), which is a quick way to switch off one integration without touching code or the org's other callers.

## Attribution &amp; reporting

Each source's spend and token usage are tracked separately and surfaced on the [Credits](/products/logicai/docs/admin-credits) tab under **This month's spend → By source**, alongside the chat bucket (chat plus any internal/background callers). This lets admins see exactly where credits are going and set limits accordingly.
