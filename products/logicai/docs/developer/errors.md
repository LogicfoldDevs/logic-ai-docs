---
title: Errors & Status Codes
description: How the LogicAI API reports failures, the status codes it returns, and how to handle them.
---

The synchronous methods (`invoke`, `invokeJson`) are designed to **never throw** for gateway, credit, or validation problems. Instead they return a `Response` with `success = false`, a `statusCode`, and a human-readable `error`. The async method (`invokeAsync`) is the exception — it validates up front and throws so the caller fails fast.

## Status codes

`Response.statusCode` is an HTTP-style code:

| Code | Meaning | Typical cause |
|---|---|---|
| **200** | Success | The call worked; `text` holds the reply. |
| **400** | Bad request | A missing or invalid field on the `Request` — no `registrationId`, or no `prompt` **and** no `contentBlocks`. |
| **402** | Insufficient credits / cap reached | The org's credit balance is too low, or a monthly [usage limit](/products/logicai/docs/admin-usage-limits) has been hit. |
| **503** | Not available | The org isn't connected/provisioned yet, or the source is disabled. |
| **500** | Unexpected error | An internal error not covered above. |

## Handling failures with `invoke`

Always check `success` before using `text`:

```apex
lai.LogicAISchema.Response res = lai.LogicAI.invoke(req);

if (res.success) {
    // res.text is safe to use
    account.AI_Summary__c = res.text;
} else {
    switch on res.statusCode {
        when 402 { /* out of credits or over a spend cap — alert an admin */ }
        when 503 { /* org not provisioned or source disabled — retry later */ }
        when 400 { /* fix the request — see res.error */ }
        when else { /* log res.error and move on */ }
    }
    System.debug(res.statusCode + ': ' + res.error);
}
```

## Exceptions

The only method that throws for these conditions is **`invokeAsync`**, which validates the request and resolves the source **synchronously** (before enqueuing) so problems surface on your transaction rather than disappearing into the async job. It throws:

```apex
try {
    lai.LogicAI.invokeAsync(req);
} catch (lai.LogicAI.LogicAIException e) {
    // Missing registrationId, empty prompt+blocks,
    // or an unregistered / disabled source.
    System.debug(e.getMessage());
}
```

`register(...)` also throws `lai.LogicAI.LogicAIException` — for a blank source name or an unknown model.

`invoke` / `invokeJson` catch everything internally, so you don't need a try/catch around them for gateway or credit failures — only ordinary Apex exceptions (e.g. hitting a governor limit in your own surrounding code) can escape.

## Common messages and what to do

| `error` contains | What it means | Fix |
|---|---|---|
| "registrationId is required" | You didn't set `Request.registrationId`. | Call `register(...)` once and pass the id it returns. |
| "does not match a registered source" | The id doesn't resolve to a source (e.g. deleted, or from another environment). | Re-register in this org and store the new id. |
| "is disabled" | The source was disabled on the Credits tab. | Re-enable it, or use a different source. |
| "requires either prompt or contentBlocks" | The request had neither text nor content. | Set `prompt`, or supply `contentBlocks`. |
| credit / payment / "402" | Balance too low or a spend cap reached. | Ask an admin to buy credits or raise the [usage limit](/products/logicai/docs/admin-usage-limits). |
| "provisioned" / "not connected" | The org's AI workspace isn't ready. | Finish [connecting](/products/logicai/docs/getting-started) and wait for activation. |
