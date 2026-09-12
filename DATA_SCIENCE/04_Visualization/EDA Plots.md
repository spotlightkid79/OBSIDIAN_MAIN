---
id: "nmr50lpktp7h6"
parent: null
position_x: 
position_y: 
color: null
---
# EDA Plots

**Folder:** [[📈 04 · Visualization]] · **Topic:** #viz #eda

## What it is
The standard battery of plots run during [[3 · Exploratory Data Analysis (EDA)|exploratory analysis]]: histograms (per feature), boxplots (outlier check), correlation heatmap, pairplot, missingness matrix.

## Key idea
Plot first, model later. Anomalies you spot here save days of debugging downstream.

## Python
```python
import seaborn as sns, matplotlib.pyplot as plt
df = sns.load_dataset("penguins").dropna()
sns.pairplot(df, hue="species"); plt.show()
sns.heatmap(df.select_dtypes("number").corr(), annot=True); plt.show()
```

## Related
- [[3 · Exploratory Data Analysis (EDA)]]
- [[Outliers]]
- [[Chart Selection]]
- [[Descriptive Statistics]]
