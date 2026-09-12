---
id: "nmr50lpkt1lre"
parent: null
position_x: 
position_y: 
color: null
---
# SQL for Data Science

**Folder:** [[🐿️ SQL]] · **Topic:** #sql #ds

## What it is
Patterns you'll use over and over: cohorts, retention, funnels, top-N per group, percentiles, sampling.

## Key idea
Push aggregation into SQL where the data lives — then pull the small result into pandas. Don't `SELECT *` 100M rows into Python.

## SQL
```sql
-- Top 3 highest-spending customers per country (window-function pattern)
WITH ranked AS (
    SELECT
        country,
        customer_id,
        SUM(total) AS spent,
        ROW_NUMBER() OVER (PARTITION BY country ORDER BY SUM(total) DESC) AS rk
    FROM orders
    GROUP BY country, customer_id
)
SELECT * FROM ranked WHERE rk <= 3;
```

## Python interop
```python
import pandas as pd
from sqlalchemy import create_engine
# engine = create_engine("postgresql+psycopg2://user:pass@host/db")
# df = pd.read_sql("SELECT * FROM ranked WHERE rk <= 3", engine)
```

## Related
- [[Window Functions]]
- [[Subqueries & CTEs]]
- [[Pandas Basics]]
- [[2 · Data Collection]]
