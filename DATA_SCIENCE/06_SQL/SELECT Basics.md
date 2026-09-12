---
id: "nmr50lpkt9imd"
parent: null
position_x: 
position_y: 
color: null
---
# SELECT Basics

**Folder:** [[🐿️ SQL]] · **Topic:** #sql

## What it is
The fundamental query: pick columns from a table, optionally with computed expressions and aliases.

## Key idea
Logical execution order is FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT — not the order you write them.

## SQL
```sql
SELECT
    id,
    UPPER(name) AS name_upper,
    salary * 12 AS annual_salary
FROM employees
ORDER BY annual_salary DESC
LIMIT 10;
```

## Related
- [[Filtering — WHERE]]
- [[Aggregations — GROUP BY]]
- [[SQL for Data Science]]
