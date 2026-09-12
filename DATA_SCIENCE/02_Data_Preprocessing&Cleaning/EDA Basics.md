---
id: "nmr50lpkt8367"
parent: null
position_x: 
position_y: 
color: null
---
# EDA Basics

## 🔹 What is EDA?

**Exploratory Data Analysis (EDA)** is the process of:
- Understanding the structure of data  
- Detecting patterns, anomalies, and relationships  
- Preparing data for modeling  

👉 Goal: **Know your data before building models**

---
## 🔹 1. Load Data

```python
import pandas as pd

df = pd.read_csv("data.csv")
```

------
## 🔹 2. Inspect Structure

```python
df.shape          # rows, columns
df.head()         # first 5 rows
df.info()         # dtypes & non-null counts
df.dtypes         # column types
df['Column'].value_counts()
```

---
## 🔹 3. Summary Statistics

```python
df.describe()              # numeric summary

df.describe(include="O")   # categorical summary, count - unique - top -  freq (defaults to columns) 
# or 
df.describe(include='all') # Combines stats and categorical counts into one table
# or
df_cat = df_train.select_dtypes(include=['object', 'category']).columns

df.nunique()               # unique values per column

# Customizes the specific quartiles or percentiles shown in the numeric summary 
df.describe(percentiles=[0.25, 0.50, 0.75])
# Explicitly targets 'object' data types; functionally identical to include="O" 
df.describe(include=['object'])


df.describe().T # Much easier to scroll through vertically
```

This command is a crucial step in **Exploratory Data Analysis (EDA)** because it helps you quickly identify:

- **High Cardinality:** If a column like "Username" has 1,000 rows and 1,000 `unique` values, it might not be useful for machine learning patterns.
    
- **Dominant Categories:** If a "Country" column has 1,000 rows and the `top` value is "USA" with a `freq` of 950, you know your data is heavily skewed toward one category.
    
- **Missing Data:** By comparing the `count` to the total number of rows in your dataset, you can see if a specific categorical column has many missing values.
---
## 🔹 4. Missing Values and Unnecessary Columns

```python
df.isnull().sum()
miss = df.isnull().mean() * 100   # % missing
print(miss[miss >= 0].sort_values(ascending=False))

import seaborn as sns
sns.heatmap(df.isnull(), cbar=False)
```

```python
(df.isna().sum()/df.shape[0]).sort_values().plot(kind='bar')
```

```python
# EDA | Dropping Unnecessary Columns (`axis=1` Logic)

#During [[3 · Exploratory Data Analysis (EDA)]] and data preprocessing, unique #identifiers (such as the `Id` column) that provide no predictive value must #be removed before feeding the data into a machine learning model.

# Drops the 'Id' column from the dataset
df = df.drop('Id', axis=1)

```
---
## 🔹 5. Duplicates

```python
df.duplicated().sum()
df.drop_duplicates(inplace=True)
```

---
## 🔹 6. Univariate Analysis

**Numeric** → distribution, skewness
```python
df["col"].hist(bins=30)
sns.boxplot(x=df["col"])
```

**Categorical** → frequency
```python
df["cat"].value_counts()
sns.countplot(x="cat", data=df)
```

---
## 🔹 7. Bivariate / Multivariate Analysis

```python
sns.scatterplot(x="x", y="y", data=df)   # num vs num
sns.boxplot(x="cat", y="num", data=df)   # cat vs num
pd.crosstab(df["a"], df["b"])            # cat vs cat
sns.pairplot(df)
```

---
## 🔹 8. Correlation

```python
corr = df.corr(numeric_only=True)
sns.heatmap(corr, annot=True, cmap="coolwarm")
---------------------------or-----------------------
plt.figure(figsize=(10, 8))
correlation_matrix = df_train.corr(numeric_only=True)
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt=".2f")
plt.title('Correlation Heatmap')
plt.show()
```

---
## 🔹 9. Outlier Detection

```python
# IQR method
Q1, Q3 = df_train["Fare"].quantile([0.25, 0.75])
IQR = Q3 - Q1

lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

outliers = df_train[(df_train["Fare"] < lower_bound) | (df_train["Fare"] > upper_bound)]

print(f"Fare Outlier Thresholds: {lower_bound} to {upper_bound}")
print(outliers.head()) # Shows the first few rows of extreme fares
```

---
## 🔹 10. Target Variable Analysis (if supervised)

- **`SalePrice`**: Bu senin tahmin etmek istediğin değer (y).
    
- _Kritik İpucu:_ Ev fiyatları genellikle sağa çarpıktır (log-normal dağılım). Modelin daha rahat öğrenmesi için bu kolona Log Dönüşümü uygulamak (`np.log1p(df['SalePrice'])`) model performansını ciddi artırır.

### Sınıflandırma (Classification) vs. Regresyon (Regression)

- **Titanic bir Sınıflandırma problemidir:** Tahmin etmek istediğin şey (`Survived`) sürekli bir sayı değil; sadece **0 (Öldü)** veya **1 (Kurtuldu)** değerleridir. İki seçenekli (binary) bir değişkendir. Sadece iki seçeneği olan bir şeyin "sağa çarpık kuyruğu" olamaz, dolayısıyla logaritmasını alarak "normal dağılıma benzetmeye çalışmak" mantıksızdır.
    
- **House Prices bir Regresyon problemidir:** Tahmin etmek istediğin şey (`SalePrice`), 35.000 ile 755.000 arasında değişen **sürekli (continuous) bir sayıdır**. Kuyruğu uzayabildiği için çarpıklık (skewness) sadece regresyon problemlerinde (ve sadece sayısal hedef değişkenlerde) bir sorun haline gelir.
### ne zaman hedef değişkene log atmalıyız?

Bir veri setinde hedef değişkene (y) log dönüşümü uygulamak istiyorsan şu 3 şartın bir arada sağlanması gerekir:

1. Problem bir **Regresyon** problemi olmalı (Sayı tahmin etmelisin).
2. Hedef değişken **sürekli sayısal** bir değer olmalı (Ev fiyatı, maaş, ciro, tıklanma sayısı vb.).
3. Bu sayının dağılımı **sağa çarpık (pozitif skewness)** olmalı, yani veri setinde az sayıda ama aşırı büyük değerler bulunmalı.

```python
df["target"].value_counts(normalize=True)   # class balance
sns.histplot(df["target"])                  # regression target
```

-----
***DATA PROFILING HTML*

```python
from ydata_profiling import ProfileReport

profile = ProfileReport(train, title="Training Data EDA Report")
profile.to_file("train_report.html")
```





------
## ✅ EDA Checklist

- [ ] Shape & dtypes checked  
- [ ] Missing values handled  
- [ ] Duplicates removed  
- [ ] Distributions visualized  
- [ ] Outliers identified  
- [ ] Correlations explored  
- [ ] Target variable understood  

👉 **Output:** clean, well-understood dataset ready for **feature engineering** & **modeling**.
