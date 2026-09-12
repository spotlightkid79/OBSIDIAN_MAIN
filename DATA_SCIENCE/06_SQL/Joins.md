---
id: "nmr50lpkto77q"
parent: null
position_x: 
position_y: 
color: null
---
# Joins

**Folder:** [[🐿️ SQL]] · **Topic:** #sql

## What it is
Combine rows across tables on a key.
- **INNER** — rows matching in both
- **LEFT** — all left, matched right (NULL if no match)
- **RIGHT** — mirror of LEFT
- **FULL OUTER** — everything, NULL where unmatched
- **CROSS** — Cartesian product

## Key idea
Mismatch on the join key explodes or drops rows silently — always check row counts before/after.

## SQL
```sql
SELECT u.id, u.name, COUNT(o.id) AS order_count
FROM users u
LEFT JOIN orders o ON o.user_id = u.id
GROUP BY u.id, u.name;
```

## Related
- [[SELECT Basics]]
- [[Aggregations — GROUP BY]]
- [[Subqueries & CTEs]]
