---
id: "nmr50lpktlelz"
parent: null
position_x: 
position_y: 
color: null
---
# Hypothesis Testing

**Folder:** [[📊 01 · Statistics & Mathematics]] · **Topic:** #statistics

## What it is
A formal way to ask "is this difference real or just chance?". State a null (H₀) and alternative (H₁), compute a test statistic, get a p-value, reject H₀ if p < α (usually 0.05).

## Key idea
A small p-value means "the data would be unusual if H₀ were true" — not "H₁ is true with probability 1−p".

## Python
```python
from scipy import stats
a = [12, 14, 15, 13, 16]
b = [22, 19, 24, 20, 25]
t, p = stats.ttest_ind(a, b)
print(f"t={t:.3f}  p={p:.4f}")
```

## Related
- [[Distributions]]
- [[Confidence Intervals]]
- [[Correlation vs Causation]]
