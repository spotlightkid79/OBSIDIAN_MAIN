---
id: "nmr50lpktyxd5"
parent: null
position_x: 
position_y: 
color: null
---
# Probability

**Folder:** [[📊 01 · Statistics & Mathematics]] · **Topic:** #statistics

## What it is
The mathematics of uncertainty. P(A) ∈ [0, 1]. Joint, marginal, and conditional probabilities describe how events relate.

## Key idea
P(A and B) = P(A) · P(B | A). If independent, P(B|A) = P(B).

## Python
```python
import random
trials = 100_000
heads = sum(random.random() < 0.5 for _ in range(trials))
print(f"P(heads) ≈ {heads / trials:.3f}")
```

## Related
- [[Distributions]]
- [[Bayes' Theorem]]
- [[Hypothesis Testing]]
