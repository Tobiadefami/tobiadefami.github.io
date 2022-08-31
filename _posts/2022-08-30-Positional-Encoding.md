---
layout: post
author: oluwatobi adefami
title: Understanding Positional Encoding with Jax
mathjax: true
---

## Positional Encoding -- Overview

```python
import jax.numpy as jnp
import matplotlib.pyplot as plt
import numpy as np

plt.style.use('seaborn')
```

|![positional encoding](/assets/p_e.png)|
|:--:|
| <b>Fig.1 - Positional Encoding Layer of the Transformer Model</b>|

### Defining the positional encoding function

$$P.E_{(i, 2j)} = \sin(\frac{i}{n^{2j/d_{model}}})$$ 
$$P.E_{(i, 2j+1)} = \cos(\frac{i}{n^{2j/d_{model}}})$$
> where i is the position index and j is the dimension index.

using jax, we can define the function programatically like so:

```python 

def position_enc(seq, d, n=None):
    P_E = jnp.zeros((seq, d)) 
    for i in range(seq):
        for j in jnp.arange(int(d/2)):
            den = jnp.power(n, 2*j/d)
            P_E = P_E.at[i, 2*j].set(jnp.sin(i/den))
            P_E = P_E.at[i, 2*j+1].set(jnp.cos(i/den))
    return P_E

```

#### Understanding the position encoding matrix

```python

def plotSin(i, d=512, n = 10000):
    x = jnp.arange(0, 100, 1)
    den = jnp.power(n, 2*x/d)
    y = jnp.cos(i/den)
    plt.plot(x, y)
    title = f"i = {str(i)}"
    plt.title(title)
    
fig = plt.figure(figsize=(15, 4))
for i in range(4):
    plt.subplot(141 + i)
    plotSin(i*4)
```


|![positional encoding matrix](/assets/p_e_matrix.png)|
|:--:|
| <b>Fig.2 - Positional encoding matrix</b>|

