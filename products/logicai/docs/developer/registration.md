---
title: Source Registration
description: Register a source before calling the LogicAI API, and reuse its registration id.
---

Every call to the global API is attributed to a **source** — a named caller you register once. The source supplies the AI **model** and the **attribution key** (so its usage shows up separately in reporting). Registration is mandatory: the API will not run for an unregistered source.

## Registering a source

Call `register` once, at setup, and store the returned **registration id**:

```apex
Id regId = lai.LogicAI.register('NightlySync', 'claude-sonnet-4-6');
// Persist regId (e.g. in Custom Metadata or a Custom Setting) and reuse it.
```

- **Idempotent** — calling `register('NightlySync', ...)` again returns the **same** id. It won't create duplicates.
- **Don't register on every invoke.** Register once, keep the id, and pass it on each `Request.registrationId`.
- **Model** — must be a catalogued gateway model, or blank to use the org default. An unknown model is rejected at register time so you find out immediately, not at call time.
- Re-registering with a new model **updates** the source's model; re-registering with a blank model leaves an admin-set model untouched. Registration never changes the source's admin-managed settings.

Behind the scenes a source is a **Logic AI Source** record (`Bot_Source__c`), keyed on your source string. The registration id is that record's Id.

> **Breaking change (v1.63):** `registrationId` is now **required** on every `invoke` / `invokeAsync` call, and there is no fallback for unregistered callers. If you used the API before this release, add a one-time `register(...)` and pass the id it returns.

## Choosing a source name

Pick a stable, descriptive name per logical caller — e.g. `NightlySync`, `CaseClassifier`, `QuoteDrafter`. Usage and spend are tracked per source, so a good name is one an admin will recognise when reviewing spend. Reuse the same name (and id) for all calls from that integration.

## Spend limits are set by admins

Each source's spend can be capped, and a source can be enabled or disabled, by an admin — no code required. That's an org-management concern, so it lives in the admin console under [Usage Limits](/products/logicai/docs/admin-usage-limits), not here.

Two things to know as a developer:

- If a source is **disabled** or has hit its **monthly limit**, your call is refused: `invoke` returns an error (a `402` for a limit, a `503` for a disabled source) and `invokeAsync` throws. See [Errors & Status Codes](/products/logicai/docs/developer/errors).
- The source name you choose is what the admin sees when setting those limits, so pick it with that in mind.
