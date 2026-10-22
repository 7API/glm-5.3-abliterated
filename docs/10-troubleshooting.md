# Troubleshooting

## 401 Unauthorized

Missing, revoked or mistyped key. Re-copy it from the dashboard and confirm `Authorization: Bearer sk-...`.

## 404 on every path

Wrong base URL. Copy the exact URL from the dashboard. Do not add or remove `/v1` unless it is shown.

## 404 model_not_found

The GLM 5.3 model ID was renamed, retired or typed incorrectly. Copy the current ID from the dashboard.

## 400 Bad Request

Common causes:

- missing `messages` array;
- missing `max_tokens` on an Anthropic-style request;
- invalid role names;
- a field the selected GLM 5.3 variant does not support.

## 429 Too Many Requests

Rate or balance limit. Check usage and balance; add exponential backoff; reduce concurrency.

```python
import random, time

def backoff(attempt: int) -> None:
    time.sleep(min(30, (2 ** attempt) + random.random()))
```

## Streaming returns nothing

The model may not support streaming. Disable streaming and confirm a normal completion works.

## Truncated output

Increase `max_tokens`, check the model’s output limit, or shorten the prompt.

## Tool calls fail

Confirm the model supports tools, validate the JSON schema, and check the returned `tool_calls` before executing anything.

## Claude Code ignores the URL

- Confirm `ANTHROPIC_BASE_URL` is set in the launching shell.
- Check whether your version uses `ANTHROPIC_AUTH_TOKEN` or `ANTHROPIC_API_KEY`.
- Test the key with a direct request first.

## Cursor returns 404

Use the OpenAI-compatible base URL, not the Anthropic URL. Enable the custom base URL in Cursor settings.

## Still stuck?

Collect the request path, status code, error body, model ID, client version and timestamp. Contact support through [Telegram](https://t.me/seven_api). Never send your full API key.

## Next steps

- [GLM 5.3 API quickstart](./03-glm-5.3-api-quickstart.md)
- [FAQ](./08-faq.md)
- [Get an API key](https://7api.st/?utm_source=github&utm_medium=docs&utm_campaign=glm-5.3-abliterated)
