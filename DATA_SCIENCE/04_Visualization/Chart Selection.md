---
id: "nmr50lpktbkfo"
parent: null
position_x: 
position_y: 
color: null
---
# Chart Selection

**Folder:** [[📈 04 · Visualization]] · **Topic:** #viz

## What it is
Picking the right chart for the question:
- **Distribution** → histogram, KDE, boxplot, violin
- **Comparison** → bar, grouped bar
- **Trend over time** → line
- **Relationship** → scatter, hexbin, pairplot
- **Composition** → stacked bar, treemap (avoid pie when >5 slices)
- **Correlation matrix** → heatmap

## Key idea
The question dictates the chart, not the other way around.

## Python
```python
import seaborn as sns, matplotlib.pyplot as plt
penguins = sns.load_dataset("penguins")
sns.scatterplot(data=penguins, x="bill_length_mm", y="bill_depth_mm", hue="species")
plt.show()
```

## Related
- [[EDA Plots]]
- [[Seaborn]]
- [[Descriptive Statistics]]
