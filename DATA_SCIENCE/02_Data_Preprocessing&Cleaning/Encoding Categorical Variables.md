---
id: "nmr50lpkta83o"
parent: null
position_x: 
position_y: 
color: null
---
# Encoding Categorical Variables

**Folder:** [[🧹 02 · Data Manipulation & Cleaning]] · **Topic:** #cleaning

## What it is
Most models need numbers. Convert categories via:
- **One-hot** — for nominal, low cardinality
- **Label/Ordinal** — when order matters (small, medium, large)
- **Target/Frequency** — for high-cardinality features

## Key idea
Always fit the encoder on **train only**, then transform test — to avoid data leakage.

## Python
```python
import pandas as pd
df = pd.DataFrame({"color": ["red", "blue", "red", "green"]})
print(pd.get_dummies(df, columns=["color"], drop_first=True))

# Örnek
df=pd.get_dummies(df,columns=['kasa','vites','yakit'],drop_first=True)

df_train = pd.get_dummies(df_train, columns=['Sex'],drop_first=True, dtype=int)
```
** dtype= int for numerical values
## 🔗 Related

- [[01 Classification]]
- - [[Feature Engineering]]
- [[Pandas Basics]]
