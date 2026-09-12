---
id: "nmr50lpktxk1m"
parent: null
position_x: 
position_y: 
color: null
---
# 2 · Data Collection

**Folder:** [[🔄 05 · Process Flow]] · **Topic:** #process

## What it is
Pull data from databases ([[🐿️ SQL|SQL]]), APIs, files, scraping, or instrumentation. Document **provenance**, units, schema, time-zone, and refresh cadence.

## Key idea
Garbage in, garbage out. Spend more time here than feels comfortable.

## Python
```python
import pandas as pd
df = pd.read_csv("data.csv")           # files
# from sqlalchemy import create_engine
# df = pd.read_sql("SELECT * FROM users LIMIT 1000", create_engine("sqlite:///db.sqlite"))
print(df.shape, df.dtypes)
```

## Related
- [[1 · Problem Definition]] · next → [[3 · Exploratory Data Analysis (EDA)]]
- [[🐿️ SQL|SQL]]
