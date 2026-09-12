# Regression

**Folder:** [[🎯 Supervised Learning]] · **Topic:** #ml
## What it is

Predict a **continuous** target. Linear regression fits y = Xβ + ε. Variants: Ridge / Lasso ([[Regularization]]), polynomial, decision-tree / gradient-boosted regressors.
## Key idea

Evaluate with **MAE / RMSE / R²** — not accuracy.

```python
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error
import numpy as np
X = np.array([[1], [2], [3], [4], [5]])
y = np.array([2, 4, 5, 4, 5])
model = LinearRegression().fit(X, y)
print("RMSE:", mean_squared_error(y, model.predict(X), squared=False))
```

## 🔗 Related

- [[Linear Algebra]]
- [[Classification Model Evaluation]]
- [[Regularization]]
- [[Bias_Variance_Tradeoff]]
- [[06 Model Evaluation Metrics (Regression)]]
