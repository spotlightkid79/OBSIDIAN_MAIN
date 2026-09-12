# Clustering

**Folder:** [[🔍 Unsupervised Learning]] · **Topic:** #ml

## What it is
Group similar samples without labels. Methods: **K-Means** (centroid-based), **DBSCAN** (density-based), **hierarchical** (tree of merges).

## Key idea
Always [[StandardScaler_MinMaxScaler_Normalization|scale]] features first — distance-based methods are sensitive to units.

## Python
```python
from sklearn.cluster import KMeans
from sklearn.datasets import make_blobs
X, _ = make_blobs(n_samples=300, centers=4, random_state=0)
labels = KMeans(n_clusters=4, n_init=10, random_state=0).fit_predict(X)
print(labels[:10])
```

## Related
- [[StandardScaler_MinMaxScaler_Normalization]]
- [[Dimensionality_Reduction]]
- [[Supervised vs Unsupervised]]
