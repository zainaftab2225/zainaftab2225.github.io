---
title: "Basics of AI"
excerpt: "AI, Machine Leaning and much more.."
date: 2020-07-23
toc: true
---

## What is AI?

- In popular culture and fiction, the AI we see is *generalized AI*. It isn't very realistic.
- A machine is said to have **artificial intelligence** if it can *interpret data*, potentially *learn from the data* and use that knowledge to adapt and *achieve certain goals*.
- A simple example of a computer with AI is detecting whether it is you in a photo or not.
- The concept was first realized in the Darthmouth conference 1956 but there was an AI winter due to a lack of *computing power* and *data*.
- These problems were solved with time (after ~2005) with more computing power and the internet.


## Machine Learning Principles and Applications

### Supervised Learning

- Computers to have to learn before they can do anything; just like humans.
- There are three main types of learning:
  1. Reinforcement Learning
  2. Unsupervised Learning
  3. Supervised Learning
- **Reinforcement Learning:** The process of learning in an environment through feedback from an AI's behavior. Think about how a baby learns to walk; the baby keeps stumbling until one day he/she learns to balance and walk properly.
- **Unsupervised Learning:** The process of learning without training labels. It can also be called clustering or grouping.
- **Supervised Learning:** The process of learning *with* training labels. The supervisor knows the correct answer and points out mistakes during the learning process.
- An easy example would be to classify images of animals which are mammals or not. This AI needs to be *trained* by examples after which it should be able to classify images it hasn't seen before. Another example is how spam emails are classified.
- Inspired by human brains and neurons, psychologist Frank Rosenblatt created the Perceptron to classify whether a shape is a triangle or not a triangle. Now, we just program our computers to behave like neurons.
- Below is a simple example of how to use a step function as an activation function to either get true or not true (false). Neurons have inputs and weights that are added and if they go above the threshold weight called the bias (can be adjusted), the neuron will output a 1 otherwise a 0.

![image-center](/images/computerscience/supervised_learning_01.JPG){: .align-center}

- There are many different kind of functions that we can use. It doesn't have to be a step function. Some more functions are given below.

![image-center](/images/computerscience/supervised_learning_02.JPG){: .align-center}

- **Precision:** How much you should trust your program when it says it has found something e.g. it tells you it found 10 triangles and out of those, 8 were actually triangles. So precision is 80%.
- **Recall:** How much your program can find the thing from the data you're actually looking for e.g. there were 200 triangles in the data set out of which it found 10 of which 8 were actually triangles. So the recall is 8/200*100 = 4%. That's a pretty bad recall rate.
