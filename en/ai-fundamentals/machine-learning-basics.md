---
guid: 0f9ffa5e-67b3-401e-8b7d-6a95031176a5
title: Machine learning basics
seo:
  title: Machine learning basics
display:
  toc: true
  outline: true
feedback:
  comments: true
---

Machine learning (ML) is the branch of AI in which a system learns to perform a task from data instead of following hand-written rules.

## The three main types

| Type | Training data | Typical tasks |
| --- | --- | --- |
| Supervised learning | Inputs paired with the correct answer (labels). | Classification, price prediction |
| Unsupervised learning | Inputs with no labels. | Clustering customers, finding anomalies |
| Reinforcement learning | Rewards and penalties from an environment. | Game playing, robot control |

## Key terms

- **Model**: the learned function that turns an input into a prediction.
- **Features**: the measurable properties of an input, such as the words in an email.
- **Training**: adjusting the model's parameters so its predictions match the examples.
- **Inference**: using the trained model on new data.

## A typical workflow

1. **Define the problem.** Decide what you predict and how you measure success.
2. **Prepare the data.** Clean it, label it and split it into training, validation and test sets.
3. **Train the model.** Fit it to the training set.
4. **Evaluate it.** Measure its performance on data it has not seen.
5. **Deploy and monitor it.** Put it into use and watch for accuracy that drifts over time.

## Overfitting and underfitting

A model **overfits** when it memorises the training data and performs poorly on new data. It **underfits** when it is too simple to capture the patterns at all. Holding back a test set that the model never trains on is the standard way to catch both.
