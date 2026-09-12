---
id: "nmr50lpkt7utm"
parent: null
position_x: 
position_y: 
color: null
---
# NumPy Basics

**Folder:** [[🧹 02 · Data Manipulation & Cleaning]] · **Topic:** #numpy

## What it is
N-dimensional arrays with vectorized math. The numerical foundation that pandas, scikit-learn, and PyTorch are built on.

## Key idea
Operations apply element-wise; broadcasting lets arrays of compatible shapes interact without explicit loops.

## Python
```python
import numpy as np
a = np.arange(10)
print(a * 2)              # vectorized
print(a.reshape(2, 5))    # reshape
print(a[a > 5])           # boolean mask
```

## Related
- [[Pandas Basics]]
- [[Linear Algebra]]
- [[StandardScaler_MinMaxScaler_Normalization]]
