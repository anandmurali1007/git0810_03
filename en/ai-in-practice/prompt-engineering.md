---
guid: d598c9b5-e27f-4ffb-ac4c-e429ee0840f4
title: Prompt engineering
seo:
  title: Prompt engineering
display:
  toc: true
  outline: true
feedback:
  comments: true
---

Prompt engineering is the practice of writing inputs that get consistent, useful results from a language model.

## Elements of a good prompt

| Element | Why it helps | Example |
| --- | --- | --- |
| Clear task | The model knows exactly what to produce. | "Summarise this article in three bullet points." |
| Context | The model understands the situation and audience. | "The readers are new support agents." |
| Constraints | The output fits your format and length. | "Use plain English. No more than 60 words." |
| Examples | The model copies the pattern you want. | One sample input with its ideal output |

## Techniques

- **Give the model a role.** "You are a technical editor" sets expectations for tone and focus.
- **Show, don't only tell.** Two or three examples (few-shot prompting) often work better than a long description.
- **Ask for reasoning first.** For multi-step problems, ask the model to work through the steps before giving the answer.
- **Separate instructions from data.** Put source material inside clear delimiters, such as XML tags, so the model does not confuse it with instructions.
- **Specify the output format.** Ask for JSON, a table or a fixed set of headings when another system reads the result.

## Iterate and test

1. Start with a simple prompt.
2. Run it on a handful of realistic inputs.
3. Note where the output is wrong, then change one thing at a time.
4. Keep the inputs as a small test set and rerun them whenever you change the prompt.

See [Evaluating AI systems](evaluating-ai-systems.md) for how to turn this into a repeatable check.
