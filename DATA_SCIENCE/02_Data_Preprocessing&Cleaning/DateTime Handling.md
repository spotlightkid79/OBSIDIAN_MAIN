---
id: "nmr50lpkt8z2r"
parent: null
position_x: 
position_y: 
color: null
---
# DateTime Handling

**Folder:** [[🧹 02 · Data Manipulation & Cleaning]] · **Topic:** #cleaning

## What it is
Time data carries hidden features: weekday, hour, month, holidays, lag, rolling stats. Always parse strings to `datetime` first.

## Key idea
Time-zone bugs and look-ahead leakage are the two classic traps.

## Python
```python
import pandas as pd
df = pd.DataFrame({"ts": pd.to_datetime(
    ["2026-01-01 09:00", "2026-01-02 14:30", "2026-01-03 22:00"]
)})
df["weekday"] = df["ts"].dt.day_name()
df["hour"] = df["ts"].dt.hour
df["is_weekend"] = df["ts"].dt.weekday >= 5
print(df)
```

## 🔗 Related
- [[Feature Engineering]]
- [[Pandas Basics]]
