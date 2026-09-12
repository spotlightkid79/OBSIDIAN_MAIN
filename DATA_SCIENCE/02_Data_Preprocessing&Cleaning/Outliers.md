---
id: "nmr50lpktxaup"
parent: null
position_x: 
position_y: 
color: null
---
# Outliers

**Folder:** [[🧹 02 · Data Manipulation & Cleaning]] · **Topic:** #cleaning
## What it is
Values far from the rest. Detect via **IQR** (1.5 × IQR rule), **Z-score** (>3), or model-based methods (Isolation Forest). Decide: keep, cap (winsorize), or remove.
## Key idea
Outliers can be errors or the most interesting signal. Investigate before deleting.
## Python
```python
import numpy as np
x = np.array([10, 11, 12, 13, 14, 15, 100])
q1, q3 = np.percentile(x, [25, 75])
iqr = q3 - q1
mask = (x >= q1 - 1.5*iqr) & (x <= q3 + 1.5*iqr)
print("clean:", x[mask])
```
- **Analysis (IQR):** ```python Q1, Q3 = df['val'].quantile([0.25, 0.75]) IQR = Q3 - Q1 outliers = df[(df['val'] < Q1 - 1.5 * IQR) | (df['val'] > Q3 + 1.5 * IQR)]
- **Treatment (Capping):** `df['val'] = df['val'].clip(lower=lower_bound, upper=upper_bound)`

# 🧠 Data Science: Outlier Management & Binning Strategies

## 1. The Outlier-Binning Relationship

**Outliers** often represent extreme but valid data (e.g., the $512 Titanic Fare). While standard statistical bounds (IQR) flag them, **Binning** is the strategy of choice when you want to preserve the _meaning_ of the extreme data without letting the _magnitude_ skew the model.

---
## 2. Detection: The IQR Method

Before binning, we identify the extent of the outlier problem using the **Interquartile Range (IQR)**.

Python
```
Q1, Q3 = df["Fare"].quantile([0.25, 0.75])
IQR = Q3 - Q1

lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

# Identify passengers outside these bounds
outliers = df[(df["Fare"] < lower_bound) | (df["Fare"] > upper_bound)]
```

---
## 3. Treatment: Binning Methods (Discretization)

### A. Quantile-Based Binning (`pd.qcut`)

**Logic:** Divides data into N bins with equal passenger counts.

- **Pros:** Neutralizes the "power" of the $512 outlier. It simply becomes part of the "Top 25%" group.
- **Cons:** Can group very different price points together to maintain equal counts.
    
Python
```
# Create 4 equal-sized groups
df['FareBin'], bins = pd.qcut(df['Fare'], 4, retbins=True, labels=[0, 1, 2, 3])
```
### B. Manual/Value-Based Binning (`pd.cut`)

**Logic:** Divides data based on specific numerical boundaries (Domain Knowledge).

- **Pros:** Respects historical/social context (e.g., defining "Luxury" as > $100).    
- **Cons:** Can result in imbalanced bins if the data is highly skewed.
    
Python
```
# Custom edges: Economy, Standard, Premium, Luxury
custom_bins = [-0.01, 8, 15, 31, 600] 
df['FareBin'] = pd.cut(df['Fare'], bins=custom_bins, labels=[0, 1, 2, 3])
```

---
## 4. Professional Workflow: The "Fit-Transform" Rule

**Crucial:** To avoid **Data Leakage**, you must calculate the bin boundaries on the **Training Set** and apply them to the **Test Set**. Do not calculate new quantiles for the test set.

Python
```
# 1. Fit to Training Data
df_train['FareBin'], train_bins = pd.qcut(df_train['Fare'], 4, retbins=True, labels=[0, 1, 2, 3])

# 2. Transform Test Data using Train's boundaries
df_test['FareBin'] = pd.cut(df_test['Fare'], bins=train_bins, labels=[0, 1, 2, 3], include_lowest=True)

# 3. Drop original columns (Redundancy & Outlier Removal)
df_train.drop(columns=['Fare'], inplace=True)
df_test.drop(columns=['Fare'], inplace=True)
```

---
## 5. Model Impact Summary

| Model Type                     | Sensitivity to Outliers | Recommended Treatment                            |
| ------------------------------ | ----------------------- | ------------------------------------------------ |
| **Linear/Logistic Regression** | **High**                | Binning or Log-Trans is **Mandatory**.           |
| **KNN / SVM**                  | **High**                | Outliers distort distance calculations.          |
| **Random Forest / XGBoost**    | **Low**                 | Binning is optional but helps simplify the tree. |
## 🔗 Related
- [[Descriptive Statistics]]
- [[Missing Values]]
- [[EDA Plots]]
- [[Feature Engineering]]    
- [[Missing Values]]
- [[02 Random_Forest (Classifier - Ensamble Method)]]
