---
id: "nmr50lpkt138e"
parent: null
position_x: 
position_y: 
color: null
---
# Bayes' Theorem

**Folder:** [[📊 01 · Statistics & Mathematics]] · **Topic:** #statistics

## What it is
Update beliefs given evidence:  **P(A|B) = P(B|A) · P(A) / P(B)**.

The base rate (P(A)) matters as much as the test accuracy — ignoring it leads to the famous "false-positive paradox" in rare-disease testing.

## Key idea
Posterior ∝ Likelihood × Prior.

## Python
```python
# Disease prevalence 1%, test sensitivity 99%, specificity 95%
prior = 0.01
sens, spec = 0.99, 0.95
p_positive = sens * prior + (1 - spec) * (1 - prior)
posterior = sens * prior / p_positive
print(f"P(disease | +test) = {posterior:.3f}")  # ~0.167
```

## Related
- [[Probability]]
- [[01 Classification]]
- [[Hypothesis Testing]]
