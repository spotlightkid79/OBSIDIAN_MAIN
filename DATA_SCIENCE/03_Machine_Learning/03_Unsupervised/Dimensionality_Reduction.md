# Dimensionality Reduction

**Folder:** [[🔍 Unsupervised Learning]] · **Topic:** #ml

## What it is
Compress many features into fewer while keeping the signal. **PCA** (linear, variance-maximizing), **t-SNE** / **UMAP** (non-linear, for visualization).

## Key idea
Reduces noise, speeds training, enables 2-D visualization — but components lose interpretability.

## Python
```python
from sklearn.decomposition import PCA
from sklearn.datasets import load_iris
X, _ = load_iris(return_X_y=True)
X2 = PCA(n_components=2).fit_transform(X)
print(X2[:5])
```

## Related
- [[Linear Algebra]]
- [[StandardScaler_MinMaxScaler_Normalization]]
- [[Clustering]]
