---
id: "nmr50lpkt5wx0"
parent: null
position_x: 
position_y: 
color: null
---
# Missing Values

**Folder:** [[🧹 02 · Data Manipulation & Cleaning]] · **Topic:** #cleaning

## What it is
NaN/None entries. Options: **drop** (when rare), **impute** (mean/median/mode, KNN, model-based), or **flag** (add a "was_missing" indicator).
## Key idea
Missingness can be informative — sometimes the *fact* a value is missing predicts the target.
## Python
```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.DataFrame({"a": [1, np.nan, 3], "b": [np.nan, 2, 3]})
print(df.isna().sum()) # or print(df.isnull().sum())
df_imputed = df.fillna(df.median(numeric_only=True))

sns.heatmap(df.isnull(),cbar=False, cmap='viridis')
plt.show
```
- **Deletion:** `df.dropna(inplace=True)`
- **Imputation:** `df['age'].fillna(df['age'].median(), inplace=True)`
- **Flagging:** `df['was_missing'] = df['salary'].isnull().astype(int)`

Instead of losing missing values by dropping the column immediately, we may convert the "presence" of data into a binary feature (1 or 0).

```python
# 1. Create the indicator: 1 if cabin is known, 0 if it is NaN 
df_train["HasCabin"] = df_train["Cabin"].notna().astype(int) 

# 2. Drop the original messy column 
df_train.drop(columns=["Cabin"], inplace=True)
```

The standard industry practice is to use the **Highest Frequency (The Mode)**.
Some analysts worry that adding more to the "Mode" makes the model too biased toward the majority.
```python
df_train['Embarked'] = df_train['Embarked'].fillna('S')
```

---
# 🧠 ML Preprocessing: Missing Data

## 1. Statistical Imputation (Simple)

- **Median/Mean**:
```python
df['col'].fillna(df['col'].median(), inplace=True)
```
    
- **Mode (Categorical)**:    
```python
df['cat'].fillna(df['cat'].mode()[0], inplace=True)
```

## 2. Model-Based Imputation

- **KNN Imputer**: Uses proximity to fill gaps. #K-Nearest_Neighbour
```python
from sklearn.impute import KNNImputer
imputer = KNNImputer(n_neighbors=5)
df_filled = imputer.fit_transform(df)
```
    
- **Iterative (MICE)**: Predicts missing values via regression.
```python
from sklearn.experimental import enable_iterative_imputer
from sklearn.impute import IterativeImputer
it_imp = IterativeImputer()
df_filled = it_imp.fit_transform(df)
```
## 3. Deletion Strategies

- **Drop Rows**:
	**Why:** Removing these rows won't bias your model because the remaining data is still a representative sample of the population.
	**Action:** Drop if the volume of missing rows is small (<5%).
	The feature is missing >60−70% of its values. It’s usually too "noisy" to save.
    The feature has zero correlation with your target.
```python
df.dropna(axis=0, inplace=True)
```

- **Drop Columns**:
- The missingness is "Missing Completely at Random" (MCAR).
- You have a massive dataset and losing 1−2% of rows won't hurt.
- The **Target variable** (y) is missing (never impute the label!).
```python
df.drop('column_name', axis=1, inplace=True)
# or 
df.dropna(subset=['target'])
# Or drop if thresh of non-missing values isn't met
df.dropna(thresh=len(df)*0.7, axis=1) 
```
## 📓 Obsidian Notes: Deletion Logic

### 🚀 Deletion Decision Matrix

- **Target is NaN**: 100% Drop.
- **MCAR + Small %**: Drop (Safe). (MCAR- Missing Completely at Random)
	- **Condition:** Missing Completely at Random (e.g., a one-off equipment glitch) and affects <5% of data. 
	- **Logic:** Since it's truly random, removing these rows won't change the overall "shape" or distribution of your data.
	- **Action:** `df.dropna()`
- **MAR/MNAR**: Avoid dropping (introduces Bias). (Missing at Random, Missing not at Random)
	- **Condition:** Missingness follows a pattern (e.g., high-income earners hiding their salary
	- **Logic:** **Avoid dropping.** If you drop these, you are deleting a specific sub-group of your population, leading to a biased model that can't predict that group accurately.
	- **Action:** Use `IterativeImputer` or a `MissingIndicator`.
- **The "Noise Reduction" (Mostly Empty)**: Drop (Prevents noise).
	- **Condition:** A row has more holes than data (e.g., 80% of features are NaN).
	- **Logic:** A row with almost no information is "dead weight." Imputing too many values for one record creates a "synthetic" row that doesn't represent a real-world entity.
	- **Action:** `df.dropna(thresh=n)`
## 4. The "Missing Indicator"

- Captures the "fact" of missingness as a feature.
```python
df['col_was_missing'] = df['col'].isnull().astype(int)
```

💻 Python Quick-Check

While you can't "prove" MNAR with code alone, you can check for **MAR** by seeing if missingness correlates with other columns:

```python
# Check if 'Age' missingness correlates with 'Gender'
df.groupby('Gender')['Age'].apply(lambda x: x.isnull().mean())
```
## 🔗 Related
- [[Pandas Basics]]
- [[Outliers]]
- [[Feature Engineering]]
