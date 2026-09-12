---
id: nmr50lpkt20zc
parent:
position_x:
position_y:
color:
cssclasses:
---
# Descriptive Statistics

**Folder:** [[📊 01 · Statistics & Mathematics]] · **Topic:** #statistics

## What it is
Numbers that summarize a dataset: center (mean, median), spread (std, IQR), and shape (skew, kurtosis). The first thing you compute on any new dataset.

## Key idea
Mean tells you "typical", std tells you "how spread out", median tells you "middle when outliers exist".

## Python
```python
import numpy as np
x = np.array([2, 4, 4, 4, 5, 5, 7, 9])
print(x.mean(), np.median(x), x.std(ddof=1), np.percentile(x, [25, 75]))
```

## Related
- [[Distributions]]
- [[Outliers]]
- [[EDA Plots]]
