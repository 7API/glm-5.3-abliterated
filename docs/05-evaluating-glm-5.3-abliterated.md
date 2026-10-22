# Evaluating GLM 5.3 Abliterated

A model that answers one blocked prompt is not “evaluated.” A useful evaluation measures refusal behavior, output quality, side effects and cost — on the exact model version you plan to deploy.

## 1. Build a prompt suite

Create a small, labeled set of prompts:

- **Normal tasks** your users will send (coding, writing, analysis).
- **Previously blocked prompts** that motivated the switch.
- **Instruction-conflict prompts** that test hierarchy handling.
- **Tool-use prompts** if you run an agent.
- **Bilingual prompts** if you serve Chinese and English users.

Keep the suite in version control so results are comparable over time.

## 2. Score refusal separately from quality

Do not collapse everything into “worked / didn’t work.” Use at least two scores:

| Dimension | Scale | What it captures |
|---|---|---|
| Refusal | 0 = refused, 1 = partial, 2 = answered | Whether the model engaged |
| Quality | 1–5 | Accuracy, usefulness, style, instruction following |
| Side effects | 1–5 | Tone, repetition, tool behavior, unwanted changes |
| Cost | tokens + retries | Cost per successful task |

A model can score 2 on refusal and 1 on quality. That is not a win.

## 3. Test the exact model ID

GLM 5.3 variants are separate entries. Record:

- model ID;
- date tested;
- provider/version notes;
- temperature and other settings;
- prompt suite version.

Family names move. IDs identify a release.

## 4. Check abliteration side effects

Abliteration can affect more than refusal. Watch for:

- a more blunt or repetitive tone;
- changes in instruction following;
- different tool-call formatting;
- weaker handling of sensitive-but-benign topics;
- changes in bilingual output.

If quality drops below your threshold, an uncensored fine-tune may be a better fit than an abliterated variant.

## 5. Run a simple harness

```python
import json, os, time
from openai import OpenAI

client = OpenAI(api_key=os.environ["SEVEN_API_KEY"],
                base_url=os.environ["SEVEN_API_BASE_URL"])

prompts = json.load(open("prompts.json", encoding="utf-8"))
rows = []

for item in prompts:
    t0 = time.time()
    r = client.chat.completions.create(
        model=os.environ["GLM_MODEL_ID"],
        messages=[{"role": "user", "content": item["prompt"]}],
        temperature=0.7,
    )
    text = r.choices[0].message.content
    rows.append({
        "id": item["id"],
        "prompt": item["prompt"],
        "output": text,
        "latency_s": round(time.time() - t0, 2),
        "usage": r.usage.model_dump() if r.usage else None,
    })

json.dump(rows, open("results.json", "w", encoding="utf-8"), indent=2)
```

Score the outputs manually or with a rubric. Do not rely on an LLM judge alone for safety-sensitive decisions.

## 6. Re-test after updates

Keep a regression suite and rerun it when:

- the provider announces a model update;
- refusal behavior changes;
- tool-call formatting changes;
- pricing changes enough to affect model choice.

## 7. Compare cost per successful task

```text
cost_per_success = total_cost / number_of_successful_tasks
```

Include retries and failed attempts. A cheaper model that needs three tries can cost more than a stronger model that succeeds once.

## 8. Document the decision

Write down:

- which model you chose;
- why it beat the alternatives;
- known side effects;
- fallback model;
- review date.

This makes it easier to revisit the choice when a new GLM 5.3 version arrives.

## Next steps

- [Abliterated vs. uncensored](./02-abliterated-vs-uncensored.md)
- [Use cases](./06-use-cases.md)
- [Safety and responsible use](./07-safety-and-responsible-use.md)
- [Get an API key](https://7api.st/?utm_source=github&utm_medium=docs&utm_campaign=glm-5.3-abliterated)
