---
id: "nmr50lpktuhhv"
parent: null
position_x: 
position_y: 
color: null
---
# Indexes & Performance

**Folder:** [[🐿️ SQL]] · **Topic:** #sql #performance

## What it is
Indexes are auxiliary data structures (usually B-trees) that speed up lookups, joins, and sorts on indexed columns — at the cost of slower writes and extra storage.

## Key idea
- Index columns used in `WHERE`, `JOIN`, `ORDER BY`
- `EXPLAIN` (or `EXPLAIN ANALYZE`) to see the query plan
- Don't index everything — write amplification & wasted memory

## SQL
```sql
CREATE INDEX idx_orders_user_date ON orders(user_id, created_at);

EXPLAIN ANALYZE
SELECT * FROM orders WHERE user_id = 42 ORDER BY created_at DESC;
```

## Related
- [[Joins]]
- [[Filtering — WHERE]]
