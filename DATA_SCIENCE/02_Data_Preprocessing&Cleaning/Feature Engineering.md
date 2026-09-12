---
id: "nmr50lpkt4gli"
parent: null
position_x: 
position_y: 
color: null
---
# Feature Engineering

**Folder:** [[🧹 02 · Data Manipulation & Cleaning]] · **Topic:** #cleaning #ml

## What it is
Crafting new inputs from raw data so the model can see patterns more easily — ratios, interactions, time-since-event, aggregations, binning.

## Key idea
Often more impactful than picking a fancier model. Domain knowledge wins here.

## Python
```python
import pandas as pd
df = pd.DataFrame({"price": [100, 200, 300], "qty": [1, 2, 5]})
df["revenue"] = df["price"] * df["qty"]
df["log_qty"] = (df["qty"] + 1).pipe(lambda s: s.apply(lambda x: x**0.5))
```

### 📝 Note: Alternative Title Handling

> **Strategy:** Mapping specialized titles to "Functional Groups" instead of a "Rare" bucket.
> 
> **Why?** "Rare" loses the gender/status distinction. A "Sir" (Male Noble) and a "Lady" (Female Noble) might have different survival rates due to the "Women and Children First" rule. Mapping them to "Noble" or "Professional" groups preserves more signal.
> 
> **Key Categories:** > * **Noble:** High status, high survival.
> 
> - **Professional:** High status, but often "Duty-Bound" (lower survival).
> - **Master:** The definitive signal for "Male Child."
> 
>***The Overfitting Risk*
>Overfitting happens when a model "memorizes" the specific people in your training set rather than learning a general rule.

```python
title_mapping = {
    "Mr": "Mr", "Miss": "Miss", "Mrs": "Mrs", "Master": "Master",
    "Dr": "Professional", "Rev": "Professional", "Col": "Professional", 
    "Major": "Professional", "Capt": "Professional",
    "Jonkheer": "Noble", "Lady": "Noble", "Sir": "Noble", 
    "Don": "Noble", "Dona": "Noble", "Countess": "Noble",
    "Mlle": "Miss", "Ms": "Miss", "Mme": "Mrs"
}

df_train['Title'] = df_train['Title'].map(title_mapping)
```

### 🛠 Pro-Tip: Feature Engineering

Many data analysts combine `Parch` and `SibSp` (Siblings/Spouses) to create a more powerful feature called **FamilySize**. This simplifies the model by capturing the total "Social Support" a passenger had.
```python
# +1 represents the passenger themselves
df_train['FamilySize'] = df_train['Parch'] + df_train['SibSp'] + 1

# We have extracted the signal, now remove the noise
df_train.drop(columns=['SibSp', 'Parch'], inplace=True)

df['IsAlone'] = (df['FamilySize'] == 1).astype(int)
```

### 📝 Parch vs. SibSp

> - **Parch:** Vertical family relations (Parents / Children).
> - **SibSp:** Horizontal family relations (Siblings / Spouses).
> - **Combined:** Often used to create `FamilySize` or a binary `IsAlone` (1 if family is 0, else 0).

**The Strategy:**

- If you use a **Random Forest**: Keep both. It loves these kinds of flags.
    
- If you use **Logistic Regression**: You might actually choose to drop `FamilySize` and just keep `IsAlone`, or vice-versa.

***📝 Note: The "ID Column" Rule

**Concept:** High Cardinality / Unique Identifiers.

**The Rule:** Always drop unique identifiers (IDs, Social Security numbers, internal tracking codes) before training.

```python
df_train.drop(columns=['PassengerId'], inplace=True)
```

### 📝 Note: Contextual Imputation

> **Concept:** Filling missing data using subgroups rather than the whole population.
> 
> **The Strategy:** Use a correlated feature (like `Pclass`) to determine the value for a missing numerical feature (like `Fare`).
> 
> **Why?** It maintains the distribution of the data and prevents the model from being misled by "average" values that are actually outliers for a specific subgroup.
> 
> **The Code:** `df['Fare'] = df['Fare'].fillna(df.groupby('Pclass')['Fare'].transform('median'))`

```python
df['Fare'] = df['Fare'].fillna(df.groupby('Pclass')['Fare'].transform('median'))
```


## Related
- [[Encoding Categorical Variables]]
- [[DateTime Handling]]
- [[StandardScaler_MinMaxScaler_Normalization]]
