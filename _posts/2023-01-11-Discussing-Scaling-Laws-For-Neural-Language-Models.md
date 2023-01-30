---
layout: post
author: oluwatobi adefami
title: Discussing Scaling Laws for Neural Language Models (Paper review)
mathjax: true
---


Language modeling arguably accounts for a large part of the research carried out in the machine learning world, and the success deep learning has seen in this area of research has led to the creation of various SOTA models that have approached human-level performance on certain tasks. This paper studies emperical scaling laws for language model performance on the cross-entropy loss by investigating the the power-law relationship between loss and other variables including the model size, dataset size, and the magnitude of compute used for training a given transformer model.

Essentially, The paper demystifies the speculative expecation(s) involving dependence of model performance on factors like model architecture, neural model size, amount of compute available, and dataset size. Full paper is available [here](https://arxiv.org/abs/2001.08361)

The below figure shows the relationship observed between loss and increase in the scale of model size, dataset size and compute magnitude. 

|![loss relstionship prelim](/assets/power-law-relationship1.png)|
|:--:|
| <b>Fig.1- Power-law scaling relationship between test loss and compute budget, dataset size, and model size respectively</b>|

