+++
layout = "single"
+++


# Deep learning with Python

## Chapter 1: What is deep learning

Skimmed.

AAAA


- Deep Learning: Multiple layers of learning
- Shallow Learning: Small layers of learning.

![](../deep_learning_with_python.md.images/20171226_133812_20174t4M.png)

Each layer of the network has an increasing level of abstraction

The goal for us building the neural network is finding the correct values for the weights of the neurons in the layers.

We have a **loss function** that is in charge of measuring how far we are for the expected result to adjust the weights.

The **optimizer** backpropagates the changes so we can adjust the weights correctly.

![](../deep_learning_with_python.md.images/20171226_134052_201746CT.png)


Initially these weights are random but we update them every iteration of the training.

## Chapter 2 Before we begin: the mathematical building blocks of neural networks

In machine learning a category in a classification problem is called a **class**. The data points are called **samples**. The class associated with a data point is a **label**

The basic data structure in a newtwork in keras is a layer

``` python
from keras import models
from keras import layers

network = models.Sequential()
network.add(layers.Dense(512, activation='relu', input_shape=(28 * 28,)))
network.add(layers.Dense(10, activation='softmax'))
```

In the example before we create 2 dense layers. A dense layer is a fully connected layer.

Once the network is created we need to pick three more things

- A loss function
- An optimizer
- Metrics to monitor during training and testing.

```
network.compile(optimizer='rmsprop',
                loss='categorical_crossentropy',
                metrics=['accuracy'])
```

What are tensors?

At its core a tensor is just a container for data. Normally numeric. We can say that a tensor is a generalization of matrices to a random number of dimensions.

Then a scalar is a 0 dimension tensor and a vector is a 1D tensor. Do not confuse a vector with 5D with a 1D tensor. A 5D tensor will have 5 axes and a random number of dimensions on each axis.

### Classification networks

The last layer of the network if we are classifying should have as many neurons as the number of categories to classify.


### How to choose loss functions

categorical_crossentropy : When you want to return classification of a category.
softmax : When you want to predict a value.


## Other notes


https://stats.stackexchange.com/questions/181/how-to-choose-the-number-of-hidden-layers-and-nodes-in-a-feedforward-neural-netw
