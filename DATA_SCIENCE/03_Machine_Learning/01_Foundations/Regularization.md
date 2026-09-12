# Regularization

**Folder:** [[🧱 Foundations]] · **Topic:** #ml

## What it is
Penalize large coefficients to prevent overfitting.
- **L2 (Ridge)** — shrinks all coefficients
- **L1 (Lasso)** — shrinks and zeros some out (feature selection)
- **ElasticNet** — combination

## Key idea
Tunes the [[Bias_Variance_Tradeoff|bias-variance tradeoff]] explicitly via the regularization strength α.

## Python
```python
from sklearn.linear_model import Ridge, Lasso
from sklearn.datasets import load_diabetes
X, y = load_diabetes(return_X_y=True)
print("Ridge R²:", Ridge(alpha=1.0).fit(X, y).score(X, y))
print("Lasso R²:", Lasso(alpha=0.1).fit(X, y).score(X, y))
```

## 🔗 Related
- [[Bias_Variance_Tradeoff]]
- [[Hyperparameter_Tuning]]
- [[01 Regression]]
