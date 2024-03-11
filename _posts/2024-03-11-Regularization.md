---
layout: distill
title: Regularization
description: A series of notes for revision purpose
tags: deeplearning interview
#giscus_comments: true
date: 2024-03-10 11:46:00
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
  - name: Limit model capacity 
    subsections:
      - name: Reduce network size
      - name: Weight decay
      - name: Parameter sharing
    # if a section has subsections, you can add them as follows:
    # subsections:
    #   - name: Example Child Subsection 1
    #   - name: Example Child Subsection 2
  - name: Early stopping
  - name: Emsemble methods
    subsections:
      - name: Dropout 
      - name: Probabilistic treatment 
  - name: Data augmentation
    subsections:
      - name: Noise injection
      - name: Transformations
      - name: Adversarial training



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

Overfitting is a common challenge in DL, where a model performs well on training data but fails to generalize to new, unseen data. An overfitted model is one that contains more params than can be justified by the data. Overfitting can be detected using a reserved validation set. If the validation error is much larger than that on the training set, the model might exhibit overfitting. 

Regularization is any modification to the learning algorithm to mitigate the overfitting problem. In the following, we explore some common regularization techniques, including limiting model capacity, early stopping, ensemble methods, and data augmentation. 


## Limiting model capacity

This refers to constraining the complexity of a model, which aims to prevent the model from being overlly complex and capturing noise or irrelevant patterns in the training data, which can lead to overfitting. 

### Reduce network size

Use a simpler model architecture with fewer layers, neurons, or parameters. Reducing the model size can make it less prone to memorizing the training data and more likely to capture essential patterns. 

### Weight decay

Or L2-regularization, is a technique used to prevent overfitting by penalizing large weights in the model. It's a regularization term (a function of weight) added to the loss function during training, and it encourages the model to use smaller weights, effectively limiting the capacity of the model. The added regularization makes the learning algorithm to perceive the input as having higher variance and thus shrinks the weights. This regularization effect is larger for weight values determined by the minor components of the data. 

### Parameter sharing

Certain parameters (weights and biases) are used across multiple parts of a model. The idea is to share learned knowledge among these parts, allowing the model to capture patterns efficiently and generalize better. 

---

## Early stopping

to be filled

---

## Ensemble methods

something

### Dropout

something


### Probabilistic treatment

---

## Data augmentation

something

### Noise injection

something 

### Transformations

someting

### Adversarial training

somehting

---

