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
- Below is a simple example of how to use a step function as an activation function to either get true or not true (false). The neuron has inputs and weights that are added and if they go above the threshold weight called the bias (can be adjusted), the neuron will output a 1 otherwise a 0.

![image-center](/images/computerscience/supervised_learning_01.JPG){: .align-center}

- There are many different kind of functions that we can use. It doesn't have to be a step function. Some more functions are given below.

![image-center](/images/computerscience/supervised_learning_02.JPG){: .align-center}

- **Precision:** How much you should trust your program when it says it has found something e.g. it tells you it found 10 triangles and out of those, 8 were actually triangles. So precision is 80%.
- **Recall:** How much your program can find the thing from the data you're actually looking for e.g. there were 200 triangles in the data set out of which it found 10 of which 8 were actually triangles. So the recall is 8/200*100 = 4%. That's a pretty bad recall rate.

### Neural Networks and Deep Learning

- What if there is more than one neuron? Our brain has ~100 billion neurons. If we connect a bunch of Perceptrons together, we can create what's called an **artificial neural network**.
- Neural networks are one of the most dominant machine learning technologies used today.
- Neural Network Architecture:
  - Input Layer
  - Output Layer
  - Hidden Layers
- A neural network is kind of a block box that does math and spits out an answer.
- In the example below, we are trying to detect a dog in a grayscale image. Each number in the input layer represents the brightness of the pixel. Each neuron in the hidden layers may focus on a complexity e.g. the curve of the nose. So it will try to detect the upper part as bright and lower part as dark and apply weights accordingly. It squishes the results between 0 and 1 and passes it to the next layer and so on. When we reach the output layer, if the value is close to 1 then the computer has actually detected a dog.

![image-center](/images/computerscience/neural_network_1.JPG){: .align-center}

- If a neural network makes a mistake, this often means that the weights aren't adjusted correctly. They need to be updated to make better predictions next time.
- **Optimization:** The task of finding the best weights for a neural network architecture is called optimization.
- **Linear regression:** Optimization strategy that attempts to model the relationship between two variables by drawing a random linear line between the variables on a graph. The summed distance between the line and each of those data points on the graph is our *error*. We've quantified how big of an error we've made. The goal of linear regression is to adjust the line to make the error as small as possible. The resultant line is called the *line of best fit* as seen below.

![image-center](/images/computerscience/neural_network_2.JPG){: .align-center}

- Some parts of the example above defy logic though. Negative people show up on a cold day and a lot of people show up on a burning hot day. To get more *accurate* results, we can use more than just temperature and number of people e.g. humidity, rain, etc. However, if we add more features, we can't visualze it and the optimization gets trickier.
