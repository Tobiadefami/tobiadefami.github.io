---
layout: post
author: oluwatobi adefami
title: Introduction to Input ids for Transformer models
mathjax: true
---


## Introduction to Input ids for Transformer models


Introduction:

We know that tokenization is an important step for natural language processing tasks, and given the advent of the transformer model [reference] and its application to various NLP tasks, it has become important to pass the right kind of inputs to the model. Tokenization alone is not sufficient as the model expects each character to undergo a process sometimes referred to as numericalization (i.e. the conversion of each character to an integer value) and by using input ids, we can map each token to a unique numerical identifier. Let's see how this works!

Given a simple sentence as input data, the first step taken towards preparing the data for the model is by tokenization. **str** objects in python are pretty much arrays under the hood, this allows us to apply character-level tokenization with a simple one-liner.


```python
txt = "I am a machine learning researcher"
tokenized_txt = list(txt)
print(tokenized_txt)
# Output
['I', ' ', 'a', 'm', ' ', 'a', ' ', 'm', 'a ', 'c', 'h', 'i', 'n', 'e', ' ', 
 'l', 'e', 'a', 'r', 'n', 'i', 'n', 'g', ' ', 'r', 'e', 's', 'e', 'a', 'r', 
 'c', 'h', 'e', 'r']

print(len(tokenized_txt))
# Output
34
```

Next step is to encode each token to a given integer:

```python
token2idx = {}
for idx, ch in enumerate(sorted(set(tokenized_txt))):
    token2idx[ch] = idx
print(token2idx)

# Output
{' ': 0, 'I': 1, 'a': 2, 'c': 3, 'e': 4, 'g': 5, 'h': 6, 
    'i': 7, 'l': 8, 'm': 9, 'n': 10, 'r': 11, 's': 12}
```
From the output, we obtain a mapping from each character in the sentence to a unique integer. With this, we can transform our tokenized text into a list of integers.

```python
input_ids = []
for token in tokenized_txt:
    input_ids.append(token2idx[token])
print(input_ids)
# Output
[1, 0, 2, 9, 0, 2, 0, 9, 2, 3, 6, 7, 10,
 4, 0, 8, 4, 2, 11, 10, 7, 10, 5, 0, 11,
 4, 12, 4, 2, 11, 3, 6, 4, 11]

assert len(input_ids) == len(tokenized_txt)
```

Looking at the output of input_ids, we see that each unique integer is represented by the exact number of times it appears in the given sentence. For example, the letter "r" is encoded as the number 11 and it appears four times in the sentence. And as expected, the number of items in the input_ids equals the number of items in tokenized_txt.

This is pretty much the idea behind how input ids are created -- omitting the final step that requires converting the array of unique integers to a 2D tensor of one-hot vectors (This will be discussed in a later post). 







