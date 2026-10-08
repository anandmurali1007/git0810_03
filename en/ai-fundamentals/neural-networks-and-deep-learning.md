---
guid: aabc1b6a-7587-46cd-ba67-1026078ba2b4
title: Neural networks and deep learning
seo:
  title: Neural networks and deep learning
display:
  toc: true
  outline: true
feedback:
  comments: true
---

A neural network is a machine learning model made of layers of simple connected units, loosely inspired by neurons in the brain. **Deep learning** uses neural networks with many layers.

## How a neural network works

- The **input layer** receives the data, such as the pixels of an image.
- **Hidden layers** transform the data step by step. Each unit combines its inputs using learned weights and passes the result through an activation function.
- The **output layer** produces the prediction, such as the probability that the image shows a cat.

During training, the network compares its predictions with the correct answers and uses **backpropagation** to adjust its weights slightly in the direction that reduces the error. Repeating this over many examples gradually improves the network.

## Common architectures

| Architecture | Suited to | Example use |
| --- | --- | --- |
| Convolutional neural network (CNN) | Images and grid-like data | Detecting defects in photos |
| Recurrent neural network (RNN) | Sequences | Early speech recognition |
| Transformer | Sequences, especially text | Large language models |

## Why deep learning took off

Three things came together in the 2010s:

1. **Large datasets**, collected from the web and digital services.
2. **Fast hardware**, especially GPUs that run many calculations in parallel.
3. **Better techniques** for training deep networks reliably.

## Trade-offs

Deep learning models can be very accurate, but they need a lot of data and computing power, and it is hard to explain why they make a particular prediction.
