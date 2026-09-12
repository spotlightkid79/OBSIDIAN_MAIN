# Cross-Validation

**Folder:** [[🧱 Foundations]] · **Topic:** #ml

## What it is
Evaluate by splitting data into **K folds**, training on K-1 and testing on 1, rotating. Average gives a more reliable score than a single train/test split.

## Key idea
Use **StratifiedKFold** for classification (preserves class ratio); **TimeSeriesSplit** for time-ordered data.

## Python
```python
from sklearn.model_selection import cross_val_score
from sklearn.ensemble import RandomForestClassifier
from sklearn.datasets import load_iris
X, y = load_iris(return_X_y=True)
scores = cross_val_score(RandomForestClassifier(n_estimators=50, random_state=0), X, y, cv=5)
print(scores, scores.mean())
```

## 🔗 Related
- [[Classification Model Evaluation]]
- [[Hyperparameter_Tuning]]
- [[Bias_Variance_Tradeoff]]
