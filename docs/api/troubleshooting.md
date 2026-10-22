# Troubleshooting API Errors

This page explains the errors the AI Assistant API returns most often and what to do about each one. Find your HTTP status code in the table below, then jump to the matching section.

| Status | Most likely cause | Can you fix it yourself? |
| --- | --- | --- |
| `401` | [Your API key is missing, invalid, or expired](#your-api-key-was-rejected) | Yes |
| `401` | [The AI Assistant's connection to the model provider failed](#the-model-provider-rejected-the-request) | No, contact support |
| `400` | [The model name is wrong](#unknown-model-name) | Yes |
| `400` | [The request is missing a required field](#missing-required-parameter) | Yes |
| `403` | [Your key or workspace isn't allowed to use that model](#model-access-denied) | Pick another model, or contact your workspace owner |
| `404` | [The URL is wrong](#wrong-url) | Yes |
| `422` | [Your workspace budget is used up](#budget-exceeded) | Wait for the reset, or contact your workspace owner |
| `429` | [The model is busy or temporarily unavailable](#model-temporarily-unavailable) | Wait and retry |
| `500`, `503` | [Problem between the AI Assistant and the model provider](#server-and-provider-errors) | Retry later, then contact support |

## Reading an error response

Most errors come back as JSON with an `error` object:

```json
{
  "error": {
    "message": "Authentication Error, No api key passed in.",
    "type": "auth_error",
    "param": "None",
    "code": "401"
  }
}
```

The `message` field tells you the most. Read it first. The `type` field names the error category, such as `auth_error`, `budget_exceeded`, or `invalid_request_error`. The `code` field repeats the HTTP status. The `param` field names the request field that caused the problem when there is one. Otherwise it's `null`, the string `"None"`, or a shortened form of your key such as `"sk-...3527"`.

The AI Assistant removes secrets, internal addresses, and file paths from messages before sending them. If part of a message reads `REDACTED`, that's why. Nothing is wrong with your request because of it.

Responses for requests that reached a model also carry an `x-litellm-call-id` header. Save it when you report a problem, because it lets us find your request in our logs.

If you use the OpenAI Python or JavaScript SDK, the SDK turns these responses into exceptions such as `AuthenticationError`, `NotFoundError`, `UnprocessableEntityError`, or `RateLimitError`. The original message is on the exception, so print it when you debug.

## Your API key was rejected

**Status: `401 Unauthorized`**

The AI Assistant couldn't verify your API key. Common messages:

| Message starts with | `type` | Meaning |
| --- | --- | --- |
| `Authentication Error, No api key passed in.` | `auth_error` | The request had no key |
| `Authentication Error, Malformed API Key passed in.` | `auth_error` | The `Authorization` header is missing the `Bearer ` prefix |
| `Authentication Error, Invalid proxy server token passed.` | `token_not_found_in_db` | The key is wrong, was deleted, or has a typo |
| `Authentication Error - Expired Key.` | `expired_key` | The key has expired. The message shows the expiry time |

To fix it:

1. Check that every request sends the key in this header:

    ```http
    Authorization: Bearer <your-api-key>
    ```

    Most tools add `Bearer ` for you. If you set the header by hand, include it once.

2. Copy the key again from your workspace. Look for missing characters and extra spaces or line breaks.
3. If the key expired or was deleted, create a new one. See [Obtaining Your API Key](api-key.md).

Sending the same key again won't help. The request fails until the key changes.

## The model provider rejected the request

**Status: usually `401`, sometimes `403`**

Your API key can be fine while the AI Assistant's own credentials for the model provider (Anthropic, OpenAI, AWS Bedrock, and others) have a problem. These messages start with `litellm.AuthenticationError` or `litellm.PermissionDeniedError`, followed by details from the provider and a line naming the model that failed. The `type` is `authentication_error`, not `auth_error`. That difference tells you the provider rejected the request, not your key.

```text
litellm.AuthenticationError: AuthenticationError: OpenAIException - Incorrect API key provided: ...

LiteLLM: model group 'example-model' failed with the error above. No fallback was attempted.
```

You can't fix this one, and a new API key won't help. Email **ai-assistant-support@list.arizona.edu** with the model name and the full error message. Try a different model while you wait.

A `503` whose `type` is `no_db_connection` is also on our side. The AI Assistant can't reach its key database for a moment. Retry in a minute or two.

## Model errors

### Unknown model name

**Status: `400 Bad Request`**

The model name in your request doesn't match any model the AI Assistant offers. The message looks like this:

```text
/chat/completions: Invalid model name passed in model=unknown-model. Call `/v1/models` to view available models for your key.
```

Use the model name exactly as the AI Assistant lists it. It can differ from the provider's own name for the same model. To see the models your key can use:

```bash
curl -s https://ai-assistant.responsibleai.arizona.edu/v1/models -H "Authorization: Bearer <your-api-key>"
```

You can also check [Current Models](../models-current.md) or the model list in your workspace.

If the name is right and you get `404` with `litellm.NotFoundError` in the message, the provider can't find the model behind that name. Contact support.

### Missing required parameter

**Status: `400 Bad Request`**

The request left out a field the endpoint needs. The `param` field names it:

```json
{
  "error": {
    "message": "/chat/completions: Missing required parameter: 'messages'.",
    "type": "invalid_request_error",
    "param": "messages",
    "code": "400"
  }
}
```

Add the field and send the request again.

### Model access denied

**Status: `403 Forbidden`**

Your key or workspace isn't allowed to use the model you asked for. The message looks like this:

```text
The requested model 'restricted-model' is not available for this API key, or the model name is invalid. Check the models available to you and try again.
```

The same message covers a model you can't use and a model name that doesn't exist, so check the spelling too. The message doesn't list the models you can use. Call `/v1/models` as shown under [Unknown model name](#unknown-model-name) to get that list.

The `type` field shows which limit applied, for example `key_model_access_denied`, `team_model_access_denied`, or `user_model_access_denied`.

Switch to a model your key can use. If you need the restricted model, ask your workspace owner or instructor to enable it.

A `403` with `litellm.PermissionDeniedError` and the message `Model is blocked` means the model is turned off for everyone. Pick a different model.

### Model temporarily unavailable

**Status: `429 Too Many Requests`**

The model is set up, but nothing can serve your request right now, usually because the provider is overloaded or recently returned errors. The message starts with `No deployments available` and often includes `Try again in <seconds> seconds`. The `type` is usually `all_deployments_in_cooldown`.

Check the response for a `Retry-After` header and wait that long before you retry. Without one, wait a few seconds and back off further on each retry. If it keeps happening, switch to another model.

## Budget exceeded

**Status: `422 Unprocessable Entity`**

Your workspace, team, or key has spent its usage allocation. The `type` field is `budget_exceeded`, and the message shows how much has been spent:

```text
Budget has been exceeded! Team=team-example Current cost: 10.5, Max budget: 10.0
```

Retrying won't help. Requests work again when:

- the budget resets at the start of the next period (Personal Workspaces get a monthly allocation), or
- your workspace owner or instructor raises the budget.

With the OpenAI SDK, this error raises `UnprocessableEntityError`. If your code treats every `429` as "out of budget", update it. A `429` now means a busy model or a rate limit, which a retry can fix. A message with `litellm.RateLimitError` means the provider is rate limiting, not that your budget ran out.

## Wrong URL

**Status: `404 Not Found`**

If the URL doesn't match any AI Assistant endpoint, the response is just:

```json
{
  "detail": "Not Found"
}
```

Check the base URL in your tool or code:

- For OpenAI-compatible tools and SDKs, the base URL is `https://ai-assistant.responsibleai.arizona.edu/v1`. The client adds `/chat/completions` itself, so don't add it to the base URL.
- If you call the API directly, chat requests go to `POST https://ai-assistant.responsibleai.arizona.edu/v1/chat/completions`.
- Watch for a doubled path such as `/v1/v1/chat/completions`, or a missing `/v1`.
- Some tools need a different form of the URL. Follow the setup page for your tool, for example [Claude Code](api-key-claude.md) or [Goose](goose_desktop.md).

A `405 Method Not Allowed` means the URL exists but you used the wrong HTTP method, for example `GET` where the endpoint expects `POST`.

## Server and provider errors

These errors come from the connection between the AI Assistant and the model provider. You can't fix them yourself.

| Status | Message mentions | Meaning |
| --- | --- | --- |
| `404` | `litellm.NotFoundError` | The provider can't find the model or endpoint |
| `500` | `litellm.InternalServerError`, often with `Connection error.` | The AI Assistant couldn't connect to the provider |
| `503` | `litellm.ServiceUnavailableError` | The provider is down or overloaded |

The AI Assistant retries some of these automatically and can fall back to another model before it gives up. If you still see one, wait a few minutes and try again, or switch models. If it continues, email **ai-assistant-support@list.arizona.edu**.

## Errors during streaming

If you set `"stream": true`, an error can show up in two ways.

If the request fails before any text arrives, you get the normal JSON error and HTTP status described on this page.

If it fails partway through, the response has already started with status `200`, and that can't change. The stream ends with an error event instead, followed by the usual end marker:

```text
data: {"error": {"message": "...", "type": "...", "param": null, "code": "429"}}

data: [DONE]
```

Check each event for an `error` key. The `200` status alone doesn't mean the request succeeded. Use the `code` and `message` inside the event with the sections above.

## Contacting support

Include these details in your email so we can look into the problem quickly:

- the HTTP status code and the full error message
- the `x-litellm-call-id` response header, if the response has one
- the model name you requested
- the base URL and the tool or library you used
- roughly when the error happened

Never send your API key. We don't need it to investigate.
