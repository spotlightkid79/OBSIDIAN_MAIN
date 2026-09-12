---
id: "nmr50lpktlqdp"
parent: null
position_x: 
position_y: 
color: null
---
# 3 · Exploratory Data Analysis (EDA)

**Folder:** [[🔄 05 · Process Flow]] · **Topic:** #process #eda

## What it is
Get to know the data. Shape, types, missingness, distributions, relationships, outliers. Mostly visual + descriptive stats.

## Key idea
Form hypotheses; then preprocess and model with intent — not blindly.

## Python
```python
import seaborn as sns
df = sns.load_dataset("titanic")
print(df.info())
print(df.describe(include="all"))
print(df.isna().mean().sort_values(ascending=False))
```

## Related
- [[EDA Plots]]
- [[Descriptive Statistics]]
- [[Outliers]]
- next → [[4 · Preprocessing]]
