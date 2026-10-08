---
guid: db48563d-18a6-4f68-90f8-b9473a58bfb9
title: Evaluating AI systems
seo:
  title: Evaluating AI systems
display:
  toc: true
  outline: true
feedback:
  comments: true
---

Evaluation tells you whether an AI system does its job well enough to ship, and whether a change made it better or worse.

## Build an evaluation set

Collect realistic inputs with the result you expect for each one:

- Common cases that represent everyday use.
- Edge cases, such as very long, ambiguous or badly formatted inputs.
- Cases the system must refuse or escalate.

Start with 20 to 50 examples and grow the set as you find new failures.

## Ways to score output

| Method | Best for | Limitation |
| --- | --- | --- |
| Exact or rule-based checks | Structured output, classifications, required fields | Cannot judge open-ended text |
| Model-based grading | Tone, helpfulness, faithfulness to sources | The grader can be wrong, so check it against human ratings |
| Human review | Final quality checks and subtle judgements | Slow and expensive at scale |

## What to measure

- **Quality**: accuracy, completeness and faithfulness to the provided sources.
- **Safety**: harmful, biased or policy-breaking output.
- **Cost and speed**: tokens used and time to respond.

## Make it part of your process

1. Run the evaluation set before and after every change to a prompt, model or retrieval setting.
2. Block a release if key scores drop.
3. Add real failures from production to the set so the same problem is caught next time.
