---
id: "nmr50lpkt85rj"
parent: null
position_x: 
position_y: 
color: null
---
# Window Functions

**Folder:** [[🐿️ SQL]] · **Topic:** #sql

## What it is
Compute aggregates **without collapsing rows**. `OVER (PARTITION BY … ORDER BY …)`. Common ones: `ROW_NUMBER`, `RANK`, `LAG`, `LEAD`, `SUM() OVER`, `AVG() OVER`.

## Key idea
Window functions = "GROUP BY that keeps detail rows". Indispensable for running totals, ranks, period-over-period comparisons.

## SQL
```sql
SELECT
    user_id,
    order_date,
    amount,
    SUM(amount) OVER (PARTITION BY user_id ORDER BY order_date) AS running_total,
    ROW_NUMBER() OVER (PARTITION BY user_id ORDER BY order_date) AS order_seq
FROM orders;
```

## Related
- [[Aggregations — GROUP BY]]
- [[Subqueries & CTEs]]
- [[SQL for Data Science]]
