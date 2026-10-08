---
guid: 1c9c1ba3-adf4-4641-9f3e-a5e94d014455
title: Retrieval-augmented generation
seo:
  title: Retrieval-augmented generation
display:
  toc: true
  outline: true
feedback:
  comments: true
---

Retrieval-augmented generation (RAG) gives a language model relevant information from your own content at the moment it answers. The model then bases its answer on that information instead of relying only on what it learned in training.

## Why use RAG

- **More accurate answers** based on your current, trusted content.
- **Fewer hallucinations**, because the model has the facts in front of it.
- **Citations**, so readers can check the source.
- **No retraining** when your content changes. You update the index instead.

## How it works

1. **Split** your documents into short passages, or chunks.
2. **Embed** each chunk. An embedding model turns the text into a vector that captures its meaning.
3. **Store** the vectors in a search index or vector database.
4. **Retrieve** the chunks most similar to the user's question.
5. **Generate** an answer by giving the model the question and the retrieved chunks.

## Design choices

| Choice | Trade-off |
| --- | --- |
| Chunk size | Small chunks match precisely but can lose context. Large chunks keep context but add noise. |
| Number of chunks retrieved | More chunks improve coverage but cost more and can distract the model. |
| Search method | Vector search finds meaning, keyword search finds exact terms. Many systems combine both. |

## Keeping it reliable

- Tell the model to answer only from the supplied passages and to say when they do not contain the answer.
- Keep the index in sync with your published content.
- Test with real questions and check both the retrieved passages and the final answers.
