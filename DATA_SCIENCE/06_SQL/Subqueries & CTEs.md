---
id: "nmr50lpktjtki"
parent: null
position_x: 
position_y: 
color: null
---
# Subqueries & CTEs

**Folder:** [[🐿️ SQL]] · **Topic:** #sql

## What it is
- **Subquery** — a `SELECT` inside another query (in `FROM`, `WHERE`, or `SELECT`).
- **CTE (Common Table Expression)** — `WITH name AS (...)` — a named, reusable, readable subquery. Can be recursive.

## Key idea
CTEs make multi-step logic readable; one CTE per "step" beats deeply nested subqueries.

## SQL
```sql
WITH high_value AS (
    SELECT customer_id, SUM(total) AS spent
    FROM orders
    GROUP BY customer_id
    HAVING SUM(total) > 10000
)
SELECT u.name, h.spent
FROM high_value h
JOIN users u ON u.id = h.customer_id
ORDER BY h.spent DESC;
```

## Related
- [[Joins]]
- [[Window Functions]]
- [[Aggregations — GROUP BY]]
