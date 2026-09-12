---
id: "nmr50lpkt5fpx"
parent: null
position_x: 
position_y: 
color: null
---
# Duplicates

**Folder:** [[🧹 02 · Data Manipulation & Cleaning]] · **Topic:** #cleaning

## What it is
Repeated rows that bias counts and averages. May be exact (full row identical) or partial (same key, different timestamp).

## Key idea
Define what "duplicate" means for *your* problem before dropping — keys depend on context.

## Python
```python
import pandas as pd
df = pd.DataFrame({"id": [1, 2, 2, 3], "v": [10, 20, 20, 30]})
print(df.duplicated().sum())          # 1
df = df.drop_duplicates(subset=["id"], keep="first")
```
- **Removing Duplicates:** `df.drop_duplicates(inplace=True)`
- **Removing Irrelevant Data:** `df.drop(columns=['UserID', 'Timestamp'], inplace=True)`
## 🔗 Related
- [[Pandas Basics]]
- [[Missing Values]]
