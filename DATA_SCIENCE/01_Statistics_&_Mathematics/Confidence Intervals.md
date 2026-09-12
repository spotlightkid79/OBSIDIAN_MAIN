---
id: "nmr50lpkt5sez"
parent: null
position_x: 
position_y: 
color: null
---
# Confidence Intervals

**Folder:** [[📊 01 · Statistics & Mathematics]] · **Topic:** #statistics

## What it is
A range that likely contains the true parameter. A 95% CI means: "if we repeated the experiment many times, ~95% of these intervals would contain the true value".

## Key idea
A wide CI = lots of uncertainty (small sample / high variance). Narrow CI = confident estimate.

## Python
```python
import numpy as np
from scipy import stats
data = np.random.normal(50, 10, size=200)
mean = data.mean()
ci = stats.t.interval(0.95, len(data)-1, loc=mean, scale=stats.sem(data))
print(f"mean={mean:.2f}  95% CI={ci}")
```

## Related
- [[Hypothesis Testing]]
- [[Distributions]]
- [[Descriptive Statistics]]
