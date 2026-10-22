# Safety and Responsible Use

GLM 5.3 abliterated and uncensored variants reduce refusal behavior. They do not remove your responsibility. This checklist is written for teams putting these models into a product, an agent or a research pipeline.

## Lawful use

Use the model for lawful purposes. Uncensored access is not permission to produce illegal content, infringe rights, harass people, distribute malware or bypass security controls. If a request would be illegal with a standard model, it is still illegal with an abliterated one.

## Provider terms

Zhipu AI, 7API and the model providers set their own usage policies. 7API provides access; it does not override those terms. Check the policy that applies to your use case, especially for commercial products and regulated industries.

## Evaluate before deploying

Do not deploy on the strength of one successful prompt. Keep a suite that covers:

- normal user requests;
- previously blocked prompts;
- instruction conflicts and prompt injection;
- tool-use and code-generation tasks;
- bilingual output;
- sensitive topics with a defined policy.

Measure refusal rate, quality, side effects and cost per successful task. Re-run the suite after model updates.

## Guardrails

- **Input checks** for prohibited content and prompt injection.
- **Output checks** for policy violations, PII leakage and unsafe code.
- **Allowlists** for tools and external actions.
- **Human approval** for irreversible actions.
- **Rate limits** and budgets per user or subkey.
- **Logging** that lets you investigate incidents.

## Data and privacy

- Send only data you are allowed to process.
- Avoid secrets, credentials and sensitive personal data in prompts.
- Use subkeys to separate projects and revoke access cleanly.
- Check retention and logging practices for the models you use.
- Document data flows for compliance review.

## Age and audience

If your product is available to minors or a general audience, define age gates and content policies before enabling abliterated or uncensored variants.

## Incident response

1. Identify the model ID, prompt and account.
2. Disable the subkey or model if the issue is ongoing.
3. Preserve relevant logs.
4. Notify the right person internally.
5. Update the prompt, guardrail or model choice.
6. Re-test before re-enabling.

## Support

For account, billing or model-access issues, contact support through [Telegram](https://t.me/seven_api). Do not send your full API key in a support message.

## A practical rule

> Use abliterated models to reduce unnecessary friction, not to remove accountability.

If you cannot explain why a request is lawful, ethical and appropriate for your audience, do not send it — regardless of what the model will answer.

## Next steps

- [Use cases](./06-use-cases.md)
- [FAQ](./08-faq.md)
- [Troubleshooting](./10-troubleshooting.md)
- [Get an API key](https://7api.st/?utm_source=github&utm_medium=docs&utm_campaign=glm-5.3-abliterated)
