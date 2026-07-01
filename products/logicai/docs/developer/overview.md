---
title: Developer Overview
description: Call Logic AI from your own Apex, Flows, and triggers with the global LogicAI API.
---

Logic AI ships a small, stable **global Apex API** so your own code — Apex classes, Flows, triggers, batch jobs, scheduled jobs — can send a prompt to Logic AI and get a reply back, using the same gateway, credits, and per-org AI workspace as the chat UI.

Use it to embed AI into your org's automation: summarise a record on update, draft a reply in a Flow, classify inbound cases in a trigger, run a nightly enrichment batch, and so on.

```apex
// One-time setup: register your caller and keep the id.
Id regId = lai.LogicAI.register('NightlySync', 'claude-sonnet-4-6');

// Every call: build a request and invoke.
lai.LogicAISchema.Request req = new lai.LogicAISchema.Request('Summarise this account in two sentences.');
req.registrationId = regId;

lai.LogicAISchema.Response res = lai.LogicAI.invoke(req);
if (res.success) {
    System.debug(res.text);
} else {
    System.debug(res.statusCode + ': ' + res.error);
}
```

## How it works

The API is a thin facade over the same single round-trip the chat uses:

- It's a **single-turn, no-tools** call. You send a prompt (and optionally files); Logic AI returns text. It does **not** run the agentic tool loop (no SOQL/DML tools) — that lives in the chat experience.
- Each call is one gateway round-trip and **debits credits** from your org's balance, exactly like a chat message.
- The **model, attribution, and spend limit** for a call come from a registered **source**, not from the request — see [Source Registration &amp; Spend Caps](/products/logicai/docs/developer/registration-spend-caps).

## The three entry points

| Method | Returns | Use when |
|---|---|---|
| `invoke(request)` | `LogicAISchema.Response` | You're in a context where a synchronous callout is allowed (e.g. a Queueable, `@future`, an LWC/aura action, an anonymous Apex script) and you want the reply back inline. |
| `invokeJson(request)` | `String` (the Response as JSON) | You just want a string to hand off — e.g. into a Flow text variable. |
| `invokeAsync(request)` | `Id` (the session id, or `null`) | You're somewhere a synchronous callout is **blocked** — a Flow, a trigger, or after DML. The call runs off-transaction; poll the session for the result. |

Full signatures and field-by-field details are in the [Apex API Reference](/products/logicai/docs/developer/apex-api).

## Namespace

All symbols are in the managed-package namespace **`lai`**: `lai.LogicAI`, `lai.LogicAISchema.Request`, `lai.LogicAISchema.Response`. The examples in these pages include the `lai.` prefix.

## Before you start

1. Your org must be **connected and provisioned** — the same setup the chat needs (see the [Quickstart](/products/logicai/docs/getting-started)). If the workspace isn't ready yet, calls return a `503`.
2. **Register your source once** and store the returned id — you pass it on every call. See [Source Registration &amp; Spend Caps](/products/logicai/docs/developer/registration-spend-caps).
3. Decide how you'll handle failures — `invoke` never throws for gateway/credit/validation problems; it reports them on the response. See [Errors &amp; Status Codes](/products/logicai/docs/developer/errors).
