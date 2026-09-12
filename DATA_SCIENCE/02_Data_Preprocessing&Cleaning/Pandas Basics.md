---
id: "nmr50lpktg2mf"
parent: null
position_x: 
position_y: 
color: null
---
# Pandas Basics

**Folder:** [[🧹 02 · Data Manipulation & Cleaning]] · **Topic:** #pandas

## What it is
The Swiss-Army knife of tabular data in Python. **DataFrame** = 2D table; **Series** = single column. Built on top of [[NumPy Basics|NumPy]].

## Key idea
Vectorized operations on whole columns are fast — avoid Python loops.

## Python
```python
import pandas as pd
df = pd.DataFrame({"name": ["Ada", "Bob", "Cy"], "age": [30, 25, 41]})
print(df.head())
print(df["age"].mean())
df["age_z"] = (df["age"] - df["age"].mean()) / df["age"].std()

df = pd.read_csv('filename.csv')
df_x = df[['column1','column2']]

class object:
	var1 = 180
	def action(self,b):
		return b + 10

ali = object()
print(ali.var1)
print(ali.action(90))

```

## Related
- [[NumPy Basics]]
- [[Missing Values]]
- [[Feature Engineering]]
