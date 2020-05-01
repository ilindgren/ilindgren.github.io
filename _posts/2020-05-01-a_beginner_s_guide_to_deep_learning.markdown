---
layout: post
title:      "A Beginner’s Guide to Deep Learning"
date:       2020-05-01 16:28:54 +0000
permalink:  a_beginner_s_guide_to_deep_learning
---

A Crash Course on Artificial Neural Networks for new Data Scientists!

The words ‘Deep Learning’ have become a staple buzz-phrase in job descriptions used by a multitude of recruiters and companies in recent years. It is an extremely complex subject that some data scientists spend years of their life studying. For many people who make career switches into data science or do not have an extensive background in artificial intelligence, it may seem like an intimidating subject to delve into. As someone in that category who had an interest in learning about it, I wrote this blog to give a brief and simple overview for people who may want an introduction to this topic.
By the end of this blog, you will be able to:
Describe effectively what deep learning is and how it differs from machine learning.
Describe artificial neural networks (ANNs) and their components.
Provide examples of real-life applications of deep learning.
What is Deep Learning?
Deep learning is a class of machine learning algorithms under the umbrella of ‘Artificial Intelligence.’ In the simplest of terms, it is teaching a machine to learn by example, much like a human baby! When reading the words ‘Artificial Intelligence’ you may think of popular science fiction films that depict robots who evolve past the point of needing humans and then eventually destroy the world. Fortunately, we have not gotten to that point yet, but machines can still do some pretty impressive things! For example, deep learning can be used to process X-ray images in order to identify irregularities like tumors. It can also be used in facial recognition, speech recognition, text classification or even to create a self-driving car!
So how is deep learning different from machine learning?
It is important to remember that deep learning IS machine learning. They both perform a function with given data and get progressively better over time. The main difference is how the data is presented to the model. Machine learning algorithms need guidance and structured data whereas deep learning networks use layers of artificial neural networks (ANN) to determine on its own if its prediction was accurate or not. This makes deep learning extremely powerful because it can deal with unstructured data (i.e. images, audio files, text data) exceptionally well.
What are Artificial Neural Networks?
Imitation is the sincerest form of flattery, and as humans, what better form of flattery is there than to model machine learning networks after the human brain?! Artificial Neural Networks (ANNs) are computing systems which are designed after the complex biological neural system inside the human brain.
Obviously, an ANN is not as complex as a human neural system, but we can visualize the similarities. In a human neuron, there are dendrites, cell bodies and axons. The dendrites receive signals from other neurons and send the signals down the cell body, do some processing and then send the signal to the axon and axon terminals were the signal is transferred to other neurons, over and over again (as shown below). In an artificial neural network, weighted inputs are fed into a feature node where some processing happens which forms an output that is then fed into the next layer, over and over again. It is important to note that the inputs and outputs are binary in nature (0 or 1). One thing that isn’t shown in the image is the gap between nodes, where weights are assigned to each input.

https://www.quora.com/What-is-the-differences-between-artificial-neural-network-computer-science-and-biological-neural-network
Weights are important because they determine which features are more important than others. Each node has a certain threshold that causes the node to ‘fire.’ If the combination of weighted inputs exceeds the threshold, it will trigger the node to signal. Since the nodes are binary, the network just acts as a typical linear regression model. By adding an activation function, it provides a non-linear transformation to the input, making it capable of learning using the difference with respect to error.
So in simpler terms, an activation function acts as a mathematical ‘gateway’ which receives the input and calculates a weighted sum with added bias to determine if the node should fire or not. This allows some connections to become stronger, causing new connections to appear, or weaker, causing connections to be eliminated. In the image below, a sigmoid activation function is being used.

Image from Flatiron School
There are many different types of activation functions that can be applied. I’ve listed a few of the most common ones below, but you can read more about them here and here:
Sigmoid Activation Function: the go-to function in the output layer of a binary classification problem. Gives an output value between 0 and 1.
Hyperbolic Tangent (tanh) Function: Performs well in intermediate layers because it gives values between -1 and +1.
Inverse Tangent (arctan) Function: Many of the same qualities as tanh, but the range goes from -1.6 to +1.6, so the slope is more gentle.
Rectified Linear Unit (RELU) Function: The most popular activation function along with tanh! The activation is exactly 0 when the output <0 which can be cumbersome when taking derivatives through.
Leaky RELU Function: solves the derivative issue RELU encounters by allowing for the activation to be slightly negative when the output <0
Real World Example
Let’s go over an example to visualize what a neural network is. Let’s say we wanted to open up a new restaurant in a town with 20 different restaurants. We want to predict the amount of sales for a restaurant given certain inputs features such as: the location, the pricing of different food items, and the variety of food choices.
Now let’s look at each feature individually:
Location — the amount of people that will pass by the restaurant are all counted as potential customers, so it makes sense that the location will help determine the volume of people passing by.
Pricing — how the food items are priced determines the affordability which in turn affects the sales amout.
Variety — having a wider range of options at a restaurant may be perceived as a higher quality restaurant and may appeal to a wider audience of customers.

Image provided by Flatiron School
So having a wider variety in food offerings may increase the perceived quality of the restaurant, but on the other hand, the if the pricing is high, customers may perceive the quality of the restaurant higher. This shows that several inputs might affect one ‘hidden’ feature. In traditional neural networks, the inputs and outputs are independent of one another, but in Recurrent Neural Networks (RNNs), the nodes can use the outputs from the previous node as an input to the current node. You can learn more about RNNs here.
A hidden layer is a layer of nodes (# of people walking by, affordability, and perceived quality in this example) whose output is dependent on the inputs (location, pricing, and variety in this example) of other nodes, and therefore is not as visible as a network output.

Image of an Artificial Neural Network from Flatiron School
To be considered ‘deep learning,’ an artificial neural network needs to have at least two hidden layers. Each layer can have any amount of nodes and there can be as many layers as you are willing to add. If you are interested in learning more about the different types of neural networks, you can learn more about it here.
Thank you for taking the time to read this blog post! I hope this gives you inspiration and confidence to learn more about deep learning.
References
https://hackernoon.com/deep-learning-vs-machine-learning-a-simple-explanation-47405b3eef08
https://www.zendesk.com/blog/machine-learning-and-deep-learning/
3. https://www.asimovinstitute.org/author/fjodorvanveen/
4. https://hackernoon.com/rnn-or-recurrent-neural-network-for-noobs-a9afbb00e860
5. https://dashee87.github.io/deep%20learning/visualising-activation-functions-in-neural-networks/
6. Flatiron School Module 6: Section 44
