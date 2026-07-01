---
title: Apex API Reference
description: Method signatures and request/response fields for the global LogicAI Apex API.
---

All symbols live in the managed-package namespace **`lai`**. These are `global` symbols: signatures are permanent and only ever added to, never changed — so code you write against them keeps working across package upgrades.

## `LogicAI` methods

### register

```apex
Id register(String source, String model)
```

Registers a **source** (a caller) and returns its **registration id**. Call this **once** at setup, store the id, and reuse it — not before every invoke. Idempotent: calling again with the same `source` returns the same id.

```apex
Id regId = lai.LogicAI.register('NightlySync', 'claude-sonnet-4-6');
```

- **`source`** — a stable, short identifier for the caller, e.g. `'NightlySync'`. Required.
- **`model`** — the AI model this source runs on. Must be a catalogued gateway model; leave blank to use the org default model.
- Throws `LogicAI.LogicAIException` if the source is blank or the model isn't recognised.

There's also a convenience overload **`register(String source)`** that registers on the org default model.

See [Source Registration &amp; Spend Caps](/products/logicai/docs/developer/registration-spend-caps) for the full picture.

### invoke

```apex
LogicAISchema.Response invoke(LogicAISchema.Request request)
```

Synchronous single round-trip. Does the gateway callout inline and returns the response.

```apex
lai.LogicAISchema.Request req = new lai.LogicAISchema.Request('Draft a follow-up email.');
req.registrationId = regId;
lai.LogicAISchema.Response res = lai.LogicAI.invoke(req);
```

**Does not throw** for gateway, credit, or validation failures — inspect `res.success` / `res.statusCode` / `res.error` instead. Must be called from a context that permits synchronous callouts (Queueable, `@future`, controller action, anonymous Apex).

### invokeJson

```apex
String invokeJson(LogicAISchema.Request request)
```

Same as `invoke`, but returns the `Response` serialised to JSON. Handy for handing a single string to a Flow text variable.

```apex
String json = lai.LogicAI.invokeJson(req);
```

### invokeAsync

```apex
Id invokeAsync(LogicAISchema.Request request)
```

Asynchronous variant for contexts where a synchronous callout **isn't** allowed — Flows, triggers, after-DML. Enqueues a Queueable that performs the gateway call off-transaction, and returns immediately.

```apex
Id sessionId = lai.LogicAI.invokeAsync(req);
```

- **A session is never created here.** Pass a `sessionId` on the request to have the reply persisted onto that `Bot_Session__c` (poll its `Bot_Message__c` rows for the result); the returned `Id` is that same session id.
- With **no** `sessionId`, the call is fire-and-forget — it runs but the reply isn't persisted, and the method returns `null`.
- Unlike `invoke`, `invokeAsync` **validates up front and will throw** `LogicAI.LogicAIException` for a bad request or an unregistered/disabled source, so the caller fails fast on their own transaction rather than silently in the async job.

## `LogicAISchema.Request` fields

Construct with `new lai.LogicAISchema.Request()` or `new lai.LogicAISchema.Request(prompt)`.

| Field | Type | Required | Notes |
|---|---|---|---|
| `registrationId` | `Id` | **Yes** | The id returned by `LogicAI.register(...)`. Identifies the source that supplies the model, spend limit, and attribution. The API will not run without it. |
| `prompt` | `String` | Yes* | The user's prompt / instruction. *Required unless you supply `contentBlocks`. |
| `sessionId` | `Id` | No | Continue an existing `Bot_Session__c` conversation. When null, the call is a stateless one-shot. |
| `systemPrompt` | `String` | No | System-prompt override. When blank, a minimal default is used — the full chat system prompt is intentionally **not** applied here. |
| `contentBlocks` | `List<Object>` | No | Structured content blocks for the user message — required for anything other than plain text (PDFs, images). See below. |

> **Deprecated fields:** `model` and `agent` are no longer honoured — the model and attribution now come from the registered source. They remain on the class only for binary compatibility; any value you set is ignored. Pass the model to `register(...)` instead.

### Content blocks (files)

To send a PDF or image, populate `contentBlocks` with Anthropic content-block maps. When set, `prompt` is appended as a trailing text block unless one is already at the end of the list.

```apex
lai.LogicAISchema.Request req = new lai.LogicAISchema.Request();
req.registrationId = regId;
req.prompt = 'Summarise this document.';
req.contentBlocks = new List<Object>{
    new Map<String, Object>{
        'type' => 'document',
        'source' => new Map<String, Object>{
            'type' => 'base64',
            'media_type' => 'application/pdf',
            'data' => EncodingUtil.base64Encode(pdfBlob)
        }
    }
};
lai.LogicAISchema.Response res = lai.LogicAI.invoke(req);
```

Images use `'type' => 'image'` with a `media_type` like `image/jpeg`.

## `LogicAISchema.Response` fields

| Field | Type | Notes |
|---|---|---|
| `success` | `Boolean` | `true` when the call succeeded; `false` when `error` is populated. |
| `statusCode` | `Integer` | HTTP-style code — see [Errors &amp; Status Codes](/products/logicai/docs/developer/errors). |
| `text` | `String` | The assistant's text reply. |
| `sessionId` | `Id` | The session used. Null for a stateless one-shot. |
| `inputTokens` | `Integer` | Input tokens consumed. |
| `outputTokens` | `Integer` | Output tokens produced. |
| `credits` | `Decimal` | Credits consumed by this call (gateway-reported). |
| `error` | `String` | Human-readable message when `success == false`. |

`Response` also exposes **`toJson()`**, which serialises it to pretty-printed JSON (this is what `invokeJson` returns).

## Governor-limit notes

- Each `invoke` performs **one HTTP callout**. It counts against the standard 100-callouts-per-transaction limit.
- `invoke` must run where callouts are allowed. In synchronous trigger/Flow contexts, use `invokeAsync`.
- Callout timeouts are set generously (120s) because model responses can take time — size your transactions accordingly.
