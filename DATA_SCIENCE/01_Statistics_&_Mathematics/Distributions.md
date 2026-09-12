---
id: "nmr50lpktc79t"
parent: null
position_x: 
position_y: 
color: null
---
# Distributions

**Folder:** [[📊 01 · Statistics & Mathematics]] · **Topic:** #statistics

## What it is
A function describing the likelihood of each possible value. Common ones: **Normal** (continuous, bell-shaped), **Bernoulli/Binomial** (success/failure), **Poisson** (counts), **Uniform** (equal chance).

## Key idea
Pick the distribution that matches your data-generating process — it determines which model and test apply.

## Python
```python
import numpy as np
import matplotlib.pyplot as plt
samples = np.random.normal(loc=0, scale=1, size=10_000)
plt.hist(samples, bins=50); plt.title("Normal(0,1)"); plt.show()
```

## Related
- [[Probability]]
- [[Hypothesis Testing]]
- [[Descriptive Statistics]]
