---
id: "nmr50lpkt47dn"
parent: null
position_x: 
position_y: 
color: null
---
# Linear Algebra

**Folder:** [[📊 01 · Statistics & Mathematics]] · **Topic:** #math

## What it is
Vectors, matrices, and the operations on them (dot products, matrix multiplication, eigenvalues). Every ML model is, under the hood, linear algebra.

## Key idea
A dataset = matrix X (rows = samples, columns = features). A model = a function from X to predictions, often via matrix operations.

## Python
```python
import numpy as np
A = np.array([[1, 2], [3, 4]])
v = np.array([1, 1])
print("A @ v =", A @ v)
eigvals, _ = np.linalg.eig(A)
print("eigenvalues:", eigvals)
```

## Related
- [[Dimensionality_Reduction]]
- [[01 Regression]]
- [[Neural_Networks_Intro]]
