---
layout: post
author: oluwatobi adefami
title: jax.vmap
mathjax: true
---

<details>
<summary>Table of Content</summary>

[unleashing the power of vectorization](#unleashing-the-power-of-vectorization-why-it-matters) 

</details>


# Unleashing the Power of Vectorization: Why It Matters 

Before delving into the specifics of `jax.vmap` and its functionalities, it is crucial to grasp the concept of vectorization and its pivotal role in crafting highly efficient code. Allow me to present an analogy that vividly portrays the significance of this technique:

Imagine being presented with a list of numbers and tasked with determining the frequency of each number within the list. One approach would involve manually counting each number individually, categorizing it, and meticulously recording the results. However, as the list grows exponentially, this method becomes increasingly inefficient.

Now, envision a remarkable device—a magical scanner capable of instantly scanning the entire list and providing you with precise information about the occurrence of each number type, sparing you the laborious process of counting them one by one.

This magical scanner mirrors the essence of vectorization, empowering you to analyze vast amounts of data simultaneously without the need for individual item counting, thereby minimizing computational costs.

Let us now explore how this concept translates into code by contrasting a brute-force approach with a vectorized approach. For the purpose of this demonstration, we will employ a large array of numbers, illuminating the distinct advantages of leveraging vectorization when dealing with extensive datasets.

We begin by examining the brute-force approach.

```python
import numpy as np

def count_numbers(numbers):
    start = time.time()
    number_counts = {}
    for number in numbers:
        if number not in number_counts:
            number_counts[number] = 1
        else:
            number_counts[number] += 1
    time_taken = time.time() - start
    print(f"total time taken: {time_taken}")
    return number_counts

if __name__ == "__main__"
    numbers = np.random.randint(10, size=1000000)
    result = count_numbers(numbers)
    print(f"result: {result}")
```
> Results from the brute-force approach

```python
>>> total time taken: 0.19865655899047852
    result: {1: 99683, 3: 100269, 8: 100111, 6: 100134, 2: 100449, 0: 100091, 9: 99932, 7: 99582, 5: 99927, 4: 99822}
```

Then we examine the vectorized approach, using just numpy.

```python
import numpy as np

def count_vectorized(numbers):
    start = time.time()
    unique_numbers, number_counts = np.unique(numbers, return_counts=True)
    number_counts_dict = dict(zip(unique_numbers, number_counts))
    time_taken = time.time() - start
    print(f"total time taken: {time_taken}")
    return number_counts_dict

if __name__ == "__main__"
    numbers = np.random.randint(10, size=1000000)
    result = count_numbers(numbers)
    print(f"result: {result}")
```
> Results from the vectorized approach

```python
>>> total time taken: 0.0037429332733154297
    result: {0: 99584, 1: 99986, 2: 99890, 3: 100535, 4: 100626, 5: 99919, 6: 100398, 7: 99599, 8: 99169, 9: 100294}
```
Running the program using the vectorized function completes in a time frame that is approximately two orders of magnitude less than the brute-force method. You are probably thinking, why does this matter? Well, put simply, the vectorized implementation runs a hundred times quicker than the brute-force approach, and that is enough reason to care! It offers improved efficiency, time savings, increased productivity, better scalability, and optimized resource utilization.





