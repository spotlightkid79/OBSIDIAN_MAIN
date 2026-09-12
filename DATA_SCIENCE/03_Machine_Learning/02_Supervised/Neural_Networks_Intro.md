# Neural Networks (Intro)

**Folder:** [[🎯 Supervised Learning]] · **Topic:** #ml #deep-learning

## What it is
Layers of weighted sums + non-linear activations. Trained by **backpropagation** (chain rule of [[Calculus for ML|calculus]]) using gradient descent.

## Key idea
Universal function approximators — but data-hungry, compute-hungry, and easy to overfit without [[Regularization|regularization]] (dropout, weight decay).

## Python
```python
import torch, torch.nn as nn
model = nn.Sequential(nn.Linear(4, 16), nn.ReLU(), nn.Linear(16, 3))
x = torch.randn(2, 4)
print(model(x).shape)  # → torch.Size([2, 3])
```

## Related
- [[Linear Algebra]]
- [[Calculus for ML]]
- [[Regularization]]
