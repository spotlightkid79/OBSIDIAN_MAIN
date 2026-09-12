---
id: "nmr50lpktwbml"
parent: null
position_x: 
position_y: 
color: null
---
# Correlation vs Causation

**Folder:** [[📊 01 · Statistics & Mathematics]] · **Topic:** #statistics

## What it is
**Correlation** = two variables move together. **Causation** = one actually drives the other. Correlation can come from a third (confounding) variable, reverse causation, or pure coincidence.

## Key idea
Only **controlled experiments** (or careful causal inference) can prove causation. Observational correlation alone cannot.

## Python
```python
import numpy as np
np.random.seed(0)
ice_cream = np.random.normal(100, 20, 100)
drownings = ice_cream * 0.05 + np.random.normal(0, 1, 100)  # both driven by heat
print("r =", np.corrcoef(ice_cream, drownings)[0, 1])  # high — but no causation
```

## Related
- [[Hypothesis Testing]]
- [[Bayes' Theorem]]
- [[Feature Engineering]]
