---
id: "nmr50lpkt3lj8"
parent: null
position_x: 
position_y: 
color: null
---
# Seaborn

**Folder:** [[📈 04 · Visualization]] · **Topic:** #viz

## What it is
Statistical plots with sane defaults — built on [[Matplotlib]]. One-liners for `histplot`, `boxplot`, `pairplot`, `heatmap`, `regplot`.

## Key idea
Pass tidy DataFrames + column names; let Seaborn handle aesthetics.

## Python
```python
import seaborn as sns
import matplotlib.pyplot as plt
tips = sns.load_dataset("tips")
sns.boxplot(data=tips, x="day", y="total_bill", hue="sex")
plt.show()
```

## Related
- [[Matplotlib]]
- [[EDA Plots]]
- [[Chart Selection]]
