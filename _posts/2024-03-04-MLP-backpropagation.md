---
layout: distill
title: Introduction to Deep Learning 
description: A series of notes for revision purpose
tags: deeplearning interview
#giscus_comments: true
date: 2024-03-03 11:46:00
thumbnail: assets/img/deepNN.jpeg

authors:
  - name: Albert Einstein
    url: "https://en.wikipedia.org/wiki/Albert_Einstein"
    affiliations:
      name: IAS, Princeton
  - name: Boris Podolsky
    url: "https://en.wikipedia.org/wiki/Boris_Podolsky"
    affiliations:
      name: IAS, Princeton
  - name: Nathan Rosen
    url: "https://en.wikipedia.org/wiki/Nathan_Rosen"
    affiliations:
      name: IAS, Princeton

bibliography: 2018-12-22-distill.bib

# Optionally, you can add a table of contents to your post.
# NOTES:
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
#   - we may want to automate TOC generation in the future using
#     jekyll-toc plugin (https://github.com/toshimaru/jekyll-toc).
toc:
  - name: Deep Learning - what is it?
    # if a section has subsections, you can add them as follows:
    # subsections:
      # - name: Example Child Subsection 1
      # - name: Example Child Subsection 2
  - name: Linear Classifier
  - name: Multi-Layer Perceptron
  - name: Backpropagation
    subsections:
      - name: Interview questions

# Below is an example of injecting additional post-specific styles.
# If you use this post as a template, delete this _styles block.
_styles: >
  .fake-img {
    background: #bbb;
    border: 1px solid rgba(0, 0, 0, 0.1);
    box-shadow: 0 0px 4px rgba(0, 0, 0, 0.1);
    margin-bottom: 12px;
  }
  .fake-img p {
    font-family: monospace;
    color: white;
    text-align: left;
    margin: 12px 0;
    text-align: center;
    font-size: 16px;
  }
---

This is the first in a series of blog notes dedicating to summarizing the most fundamental concepts in Machine Learning, Deep Learning, AI, and other scientific topics of my interest. Struggling to comprehend, distinguish, and reminisce these  concepts myself sometimes, especially before and during important interviews, I would treasure a lot a source of simple, concise, accurate information to revise for those occasions. With that in mind, I created this blog series including fundamental AI/ML concepts and relating interview questions for those preparing to launch their career in the field, or for those who simply need a refresh before moving on to more complicated concepts. If you fancy to dig deeper into these topics, you can refer to my [colleague's blog](https://ottovintola.github.io/blog/) for a more comprehensive and thorough series. 

In this first blog, we will go through the concept of Deep Learning, Linear Classifier, Multi-Layer Perception (MLP) and Backpropagation 


## Deep Learning - what is it?

**Deep Learning (DL)** is the subset of ML that focuses on the studies of Artificial Neural Networks (ANNs) with feature learning. DL architectures take in large amount of data (structured/unstructured), and use complex algorithms that utilizes multiple layers (thus "deep") to progressively extract higher-level features and hidden patterns from the raw input. For example, lower layers might identify edges of an image while higher layers identify features that can easily be perceived by human, such as a dog, or a number. 

**Feature learning** (supervised, unsupervised, self-supervised) or representation learning referes to the automatic extraction & selection of relevant features to discover useful representations or patterns *directly* from raw input. This replaces the manual feature engineering/designing process and allows automatic learning and using the features for specific tasks. 

---

## Linear Classifier

**Linear Classifier** is the simplest ML models and thus it can be considered as elementary components for DL models, which is used for binary or multiclass classification tasks. It makes prediction by combining the input features with weights, and the decision boundary is a linear combination of these features. Therefore, its effectiveness depends on the linearity of the underlying patterns. 

---

## Multi-Layer Perceptron

**MLP** is a supplement of feedforward neural network that consists of 3 types of layers: 1 input, 1 or several hidden (because the outputs of this layer are not visible outside the model ), and 1 output layer. Each node in a layer is connected to every node in the next, thus these layers are called *fully-connected*. MLP can be applied to various tasks, from classification, regression, and pattern recognition

---

## Backpropagation

**Backpropagation** is a gradient estimation used to train NN models. The key idea is to iteratively adjust the weights of the NN to reduce the error between the predicted and actual outputs. Back prob consists of *two* phases/passes:

- Forward pass: Input is fed into the NN, and the weighted sum of inputs is calculated at each neuron in each layer. Activation functions are applied to these sums to produce the output of each neuron. Then, the error or loss is calculated by comparing this output to the actual target values.  

- Backward pass: This pass involves the propagation of the error backward through the network to update the weights. The gradient of the loss function with respect to the weights is calculated using the chain rule of calculus. The weights are then adjusted in the opposite direction of the gradient to minimize the error, using done using optimization algorithm such as gradient descent. The updated weights improve the network's performance, and the process is repeated for multiple epochs until the model converges to a satisfactory solution. 

---

### Interview questions 

1. Explain the steps involved in the backpropagation algorithm and how it works in training a neural network:

  *Answer: refer to the 2 passes above*

2. What is the role of the activation function in the backpropagation algorithm? Examples of commonly used activation functions and explain when to use them?

  *Answer: Activation function introduces non-linearity into the NN, allowing it to learn complex patterns. Common activation functions include:*

    *- Rectified Linear Unit (ReLU) for hidden layers due to its simplicity and ability to mitigate the vanishing gradient problem*

    *- Sigmoid for inary classification output*

    *- Softmax for multi-class classification output to provide probability distribution over the classes*

3. How does the vanishing gradient problem affect the training of deep neural networks, and what strategies can be employed to mitigate this issue in the context of backpropagation?

  *Answer: Vanishing gradient problem occurs when gradients become extremely small during backpropagation as more layers using the same activation functions are added to the network, hindering the update of weights in earlier layers. This is because, by the chain rule, the derivatives of each layer are multiplied together (backward); thus the gradient decreases exponentially as we back-propagate to the initial layers. This is particularly problematic in deep NN.*

  *To mitigate this, we could use weight initialization methods such as He for ReLU which doesn't cause a small derivative. Alternatively, we could use non-saturating activation functions, or implement skip connections (e.g. in Residual Networks). *

4. Impact of hyperparameters (learning rate, batch size, number of epochs) on the backpropagation algorithm?

  *Answer: Learning rate determines the step size during weight updates - too high rate might lead to overshooting while too low rate leads to slow convergence. Batch size affects the efficiency of weight updates - larger batches provide smoother convergence. The number of epochs influences the duration of training. Setting these hyperparameters involves trade-offs between dataset size, computational resources, and the need for regularization.*

5. Explain the concept of weight initialization in the context of backpropagation. 

  *Answer: Weight initialization is crucial as it influences the starting point of the optimization process. Poor initialization can lead to slow convergence or getting stuck in local minima. Common techniques include He initialization for ReLU and Xavier/Glorot initialization for Sigmoid or Tanh. These methods set the initial weights that balance the variance of inputs and outputs in each layer, promoting a stable and effective training process*
