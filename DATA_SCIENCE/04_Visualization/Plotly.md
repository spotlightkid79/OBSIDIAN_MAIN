---
id: "nmr50lpktgnca"
parent: null
position_x: 
position_y: 
color: null
---
# Plotly

**Folder:** [[📈 04 · Visualization]] · **Topic:** #viz #interactive

## What it is
Interactive, web-based charts. Hover, zoom, filter. Great for dashboards (Dash) and shareable HTML.

## Key idea
Use `plotly.express` for quick exploration; drop to `graph_objects` when you need fine control.

## Python
```python
import plotly.express as px
df = px.data.iris()
fig = px.scatter(df, x="sepal_width", y="sepal_length",
                 color="species", size="petal_length", hover_data=["petal_width"])
fig.show()
```

## Related
- [[Matplotlib]]
- [[Seaborn]]
- [[7 · Deployment & Monitoring]]
