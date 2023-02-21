---
layout: post
title: Adaline Linear Neuron- Introduction and Implementation in Python
---

Artificial neural networks (ANNs) are computational models that are inspired by the structure and function of the biological neural networks in the human brain. One type of ANN is the Adaptive Linear Neuron (Adaline), which was introduced in 1960 by Bernard Widrow and Ted Hoff. In this blog post, you can find an introduction to Adaline linear neuron and demonstrate its implementation in Python.

![_config.yml]({{ site.baseurl }}/images/config.png)

Introduction to Adaline Linear Neuron

Adaline is a single-layer neural network that uses supervised learning to adjust its weights and bias to minimize the error between its output and the desired output. It consists of input nodes, a linear combiner, an activation function, and an output node. The activation function used in Adaline is linear, and it is used to compute the weighted sum of the inputs and the bias.

The goal of Adaline is to adjust its weights and bias using the gradient descent algorithm to minimize the mean square error between the predicted output and the actual output. This is done by computing the error between the predicted output and the actual output, and then adjusting the weights and bias to reduce this error.