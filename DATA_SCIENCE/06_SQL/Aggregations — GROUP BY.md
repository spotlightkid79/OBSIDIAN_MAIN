---
id: "nmr50lpkt1efa"
parent: null
position_x: 
position_y: 
color: null
---
# Aggregations — GROUP BY

**Folder:** [[🐿️ SQL]] · **Topic:** #sql

## What it is
Roll up rows into summaries. Aggregates: `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`, `STDDEV`. `HAVING` filters the resulting groups.

## Key idea
Every non-aggregated column in `SELECT` must appear in `GROUP BY`.

## SQL
```sql
SELECT
    country,
    COUNT(*)         AS users,
    AVG(age)         AS avg_age,
    SUM(revenue)     AS total_revenue
FROM users
GROUP BY country
HAVING COUNT(*) >= 10
ORDER BY total_revenue DESC;
```

## Related
- [[SELECT Basics]]
- [[Filtering — WHERE]]
- [[Window Functions]]
