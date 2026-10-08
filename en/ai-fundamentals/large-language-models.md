---
guid: 5b954105-1d1c-4b86-ab88-7bd92b679649
title: Large language models
seo:
  title: Large language models
display:
  toc: true
  outline: true
feedback:
  comments: true
---

A large language model (LLM) is a neural network trained on a very large amount of text to predict the next piece of text. That simple objective, at a large enough scale, produces models that can answer questions, write, summarise, translate and write code.

## Key concepts

- **Token**: the unit of text a model reads and writes. A token is usually a word or part of a word.
- **Context window**: the maximum number of tokens the model can consider at once, including your input and its reply.
- **Prompt**: the input you give the model, including instructions and any supporting material.
- **Parameters**: the learned weights of the model. Larger models usually have more of them.

## How LLMs are built

1. **Pre-training.** The model learns general language patterns from a broad text corpus.
2. **Fine-tuning.** The model is trained further on examples of helpful, well-formed answers.
3. **Alignment.** Human and automated feedback teach the model to follow instructions and avoid harmful output.

## What they do well

- Drafting and rewriting text in a given tone.
- Summarising long documents.
- Extracting structured data from unstructured text.
- Explaining concepts and answering questions.

## What to watch for

- **Hallucination.** A model can state false information fluently. Ground it in trusted sources where accuracy matters. See [Retrieval-augmented generation](../ai-in-practice/retrieval-augmented-generation.md).
- **Knowledge cut-off.** A model knows nothing about events after its training data was collected unless you give it that information.
- **Sensitivity to wording.** Small changes to a prompt can change the answer.
