---
id: "nmr50lpktfdrz"
parent: null
position_x: 
position_y: 
color: null
---
# 4 · Preprocessing

**Folder:** [[🔄 05 · Process Flow]] · **Topic:** #process #cleaning

## What it is
Turn EDA findings into clean, modeling-ready data: handle missing values, outliers, duplicates, encode categoricals, scale, engineer features.

## Key idea
Wrap everything in a `Pipeline` so the same transforms apply identically to train, validation, and inference data.

## Python
```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.impute import SimpleImputer
from sklearn.linear_model import LogisticRegression
pipe = Pipeline([
    ("impute", SimpleImputer(strategy="median")),
    ("scale", StandardScaler()),
    ("model", LogisticRegression(max_iter=1000)),
])
```

## Related
- [[Missing Values]] · [[Outliers]] · [[Encoding Categorical Variables]] · [[StandardScaler_MinMaxScaler_Normalization]] · [[Feature Engineering]]
- next → [[5 · Modeling]]
