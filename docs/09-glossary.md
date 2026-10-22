# Glossary

**Abliteration** — A weight-level technique that reduces a model’s refusal direction without full retraining.

**AGENTS.md** — A file of project-level instructions read by coding agents such as OpenCode and compatible tools.

**API** — Application Programming Interface; the HTTP contract your app uses to call a model.

**API gateway** — A service that routes requests to model providers and handles auth, billing and model selection.

**Anthropic-compatible** — Accepts the Anthropic Messages shape (`/messages`, top-level `system`, `max_tokens`).

**Base URL** — The root URL your SDK sends requests to. Use the exact value from the 7API dashboard.

**Cached input** — Input tokens served from a prompt cache, usually billed at a lower rate.

**Chat completion** — The OpenAI-style response format with a `choices` array.

**Context window** — The maximum number of tokens a model can consider in one request.

**GLM** — A model family from Zhipu AI, used for coding, agents, reasoning and bilingual tasks.

**GLM 5.3** — The model family covered by this repository.

**GLM 5.3 abliterated** — A GLM 5.3 variant whose weights have been modified to reduce refusal behavior.

**GLM 5.3 uncensored** — A GLM 5.3 variant that refuses less often, regardless of the method used.

**Jailbreak prompt** — A prompt or system instruction designed to change a model’s default behavior. In this repo, the files are paste-ready prompts for research and testing.

**Model ID** — The exact identifier sent in the `model` field. IDs change when providers release or retire versions.

**OpenAI-compatible** — Accepts the OpenAI chat completions shape (`/chat/completions`, `messages` array).

**Pay per token** — Billing based on input and output tokens, with no subscription.

**Prompt caching** — Reusing a processed prefix so repeated requests cost less.

**Prompt injection** — Untrusted text that tries to override system instructions.

**Refusal** — A model’s decision to decline or deflect a request.

**Streaming** — Receiving a response incrementally as tokens are generated.

**Subkey** — A separate API key funded from the main balance, used for projects or teammates.

**System prompt** — High-level instructions that set the model’s role and rules.

**Token** — The unit models use to process text.

**Tool use / function calling** — A model returning a structured call to an external function.

**Top-up** — Adding balance to the account.

## Related

- [What is GLM 5.3 Abliterated?](./01-what-is-glm-5.3-abliterated.md)
- [Abliterated vs. uncensored](./02-abliterated-vs-uncensored.md)
- [FAQ](./08-faq.md)
- [Get an API key](https://7api.st/?utm_source=github&utm_medium=docs&utm_campaign=glm-5.3-abliterated)
