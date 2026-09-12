# Ensemble Methods

**Folder:** [[🎯 Supervised Learning]] · **Topic:** #ml

## What it is
Combine many weak models into a strong one.
- **Bagging** (e.g. Random Forest) — train in parallel on bootstrap samples, average
- **Boosting** (e.g. XGBoost, LightGBM, GradientBoosting) — train sequentially, each correcting the previous
- **Stacking** — meta-model learns to combine base models

## Key idea
Boosting usually wins on tabular data; bagging reduces variance with less tuning.

## Python
```python
from sklearn.ensemble import GradientBoostingClassifier
from sklearn.datasets import load_breast_cancer
from sklearn.model_selection import cross_val_score
X, y = load_breast_cancer(return_X_y=True)
print(cross_val_score(GradientBoostingClassifier(random_state=0), X, y, cv=5).mean())
```

## Related
- [[01 Classification]]
- [[Hyperparameter_Tuning]]
- [[Bias_Variance_Tradeoff]]
