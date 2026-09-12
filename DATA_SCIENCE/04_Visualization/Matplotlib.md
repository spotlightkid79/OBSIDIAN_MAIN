---
id: "nmr50lpktn2lh"
parent: null
position_x: 
position_y: 
color: null
---
# Matplotlib

**Folder:** [[📈 04 · Visualization]] · **Topic:** #viz

## What it is
The foundational Python plotting library. Verbose, but every other library (Seaborn, pandas.plot) sits on top of it.

## Key idea
`fig, ax = plt.subplots()` then build on `ax`. Gives you full control.

## Python
```python
import matplotlib.pyplot as plt
import numpy as np
x = np.linspace(0, 2*np.pi, 100)
fig, ax = plt.subplots()
ax.plot(x, np.sin(x), label="sin")
ax.plot(x, np.cos(x), label="cos")
ax.legend(); ax.set_title("Trig"); plt.show()
```

## Related
- [[Seaborn]]
- [[Plotly]]
- [[EDA Plots]]
