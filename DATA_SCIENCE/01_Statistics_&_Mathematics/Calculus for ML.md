---
id: "nmr50lpkt1kuz"
parent: null
position_x: 
position_y: 
color: null
---
# Calculus for ML

**Folder:** [[📊 01 · Statistics & Mathematics]] · **Topic:** #math

## What it is
Derivatives tell us **how a function changes**. **Gradient descent** uses ∇loss to walk parameters downhill. The chain rule powers **backpropagation** in neural nets.

## Key idea
Train = minimize a loss. Minimize = follow the negative gradient.

## Python
```python
# Gradient descent on f(x) = (x-3)^2
x, lr = 0.0, 0.1
for _ in range(50):
    grad = 2 * (x - 3)
    x -= lr * grad
print(f"x ≈ {x:.4f}")  # → 3
```

## Related
- [[Linear Algebra]]
- [[01 Regression]]
- [[Neural_Networks_Intro]]
