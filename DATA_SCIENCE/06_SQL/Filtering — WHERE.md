---
id: "nmr50lpktw395"
parent: null
position_x: 
position_y: 
color: null
---
# Filtering — WHERE

**Folder:** [[🐿️ SQL]] · **Topic:** #sql

## What it is
Restrict rows before grouping. Combine with `AND`, `OR`, `NOT`, `IN`, `BETWEEN`, `LIKE`, `IS NULL`.

## Key idea
`WHERE` filters rows; `HAVING` filters groups (post-aggregation).

## SQL
```sql
SELECT *
FROM orders
WHERE status = 'paid'
  AND total BETWEEN 100 AND 1000
  AND created_at >= '2026-01-01'
  AND customer_id IS NOT NULL;
```

## Related
- [[SELECT Basics]]
- [[Aggregations — GROUP BY]]
