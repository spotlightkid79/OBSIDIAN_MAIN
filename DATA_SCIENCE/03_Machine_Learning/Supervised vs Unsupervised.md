---
id: "nmr50lpktm0h9"
parent: null
position_x: 
position_y: 
color: null
---
# Supervised vs Unsupervised

**Folder:** [[🤖 03 · Machine Learning]] · **Topic:** #ml

## What it is
- **Supervised** — learn f(X) → y from labeled data. Tasks: [[01 Regression]], [[01 Classification]].
- **Unsupervised** — find structure in unlabeled X. Tasks: [[Clustering]], [[Dimensionality_Reduction]].
- **Reinforcement** — learn from rewards via interaction with an environment.

## Key idea
"Do I have labels?" decides which family of algorithms applies.

## Python
```python
# Supervised: predict species from flower measurements
from sklearn.datasets import load_iris
from sklearn.linear_model import LogisticRegression
X, y = load_iris(return_X_y=True)
print(LogisticRegression(max_iter=1000).fit(X, y).score(X, y))

# Unsupervised: find 3 clusters without labels
from sklearn.cluster import KMeans
print(KMeans(n_clusters=3, n_init=10).fit_predict(X)[:10])
```

## Related
- [[01 Regression]]
- [[01 Classification]]
- [[Clustering]]
- [[Classification Model Evaluation]]
