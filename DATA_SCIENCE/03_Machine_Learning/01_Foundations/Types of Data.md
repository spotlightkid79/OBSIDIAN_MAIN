




📊 Summary Table

| **Data Type**                                    | **Sub-type**   | **Description**                                                           | **Ordered?** | **Math?** | **Expanded Examples**                                                                                                                                       |
| ------------------------------------------------ | -------------- | ------------------------------------------------------------------------- | ------------ | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Categorical**<br><br>  <br><br>_(Qualitative)_ | **Nominal**    | Distinct categories with no inherent ranking or order.                    | ❌            | ❌         | • Blood types (A, B, AB, O)<br>• Device OS (iOS, Android, Windows)<br>• Payment methods (Visa, PayPal, Cash)<br>• Animal species                            |
|                                                  | **Ordinal**    | Categories with a clear, logical order, but unequal spacing.              | ✅            | ❌         | • Customer satisfaction (CSAT) scores<br>• Economic status (Low, Middle, High)<br>• Military ranks (Captain, Major, General)<br>• Shirt sizes (S, M, L, XL) |
| **Numerical**<br><br>  <br><br>_(Quantitative)_  | **Discrete**   | Distinct, separate numerical values that are counted (whole numbers).     | ✅            | ✅         | • Number of employees in a company<br>• Bugs reported in a software sprint<br>• Items in a shopping cart<br>• Number of bedrooms in a house                 |
|                                                  | **Continuous** | Measurable values that can take any value in a range (includes decimals). | ✅            | ✅         | • Stock prices / Account balances<br>• Server response time (ms)<br>• Patient body temperature<br>• GPS Coordinates / Distance                              |

🛠️ Summary Matrix: Data Types vs. Model Fit

|**Data Type Blend**|**Best Model Choices**|**Why?**|
|---|---|---|
|**Purely Numerical**_(Continuous & Discrete)_|Linear Regression, SVM, Neural Networks, KNN, Tree-based models|Almost any model works here because the math natively accepts numbers.|
|**Heavy Categorical**_(Nominal & Ordinal)_|CatBoost, LightGBM, Naive Bayes, Decision Trees|Trees split data easily without caring about the "distance" between categories. Naive Bayes relies on probability counts rather than geometry.|
|**Mixed Data** _(Both Cat & Num)_|Random Forest, XGBoost, LightGBM|Exceptional at handling mixed data types simultaneously without requiring massive preprocessing or scaling.|



---

## 🔗 Related Machine Learning Subjects

### 🏗️ Feature Engineering & Preprocessing
* **Handling Categorical Data:**
	* [[One-Hot Encoding]] — Vital for converting **Nominal** data for Linear/Distance models.
	* [[Label Encoding & Ordinal Encoding]] — Preserving the structure of **Ordinal** data.
	* [[Target Encoding]] — Advanced technique for high-cardinality nominal features.
* **Handling Numerical Data:**
	* [[StandardScaler_MinMaxScaler_Normalization]] — Why **Continuous** data needs scaling ($Z$-score/MinMax) before hitting distance-based models.
	* [[Log Transformation]] — Fixing skewed **Discrete** counts or continuous variables for linear assumptions.
	* [[Missing Values]] — Imputation strategies differ drastically for Categorical (mode) vs. Numerical (mean/median) data.

### 🤖 Model Selection & Mechanics
* [[Distance-Based Algorithms]] — Deep dive into how KNN, K-Means, and SVM calculate geometric distances.
* [[Tree-Based Algorithms]] — Understanding how Decision Trees, Random Forests, and XGBoost split data using rule-based thresholds rather than math geometry.
* [[Generalized Linear Models]] — Linear and Logistic regression mechanics and their data type assumptions.

### 📊 Exploratory Data Analysis (EDA)
* [[Descriptive Statistics]] — Calculating Mean/Median/Standard Deviation for **Numerical** data vs. Mode/Frequency for **Categorical** data.
* [[Data Visualization Matrix]] — Choosing charts based on data type:
	* *Numerical:* [[Histograms]], [[Scatter Plots]], [[Box Plots]]
	* *Categorical:* [[Bar Charts]], [[Count Plots]], [[Pie Charts]]

### 🏷️ Vault Tags
#ml-fundamentals #feature-engineering #data-preprocessing #eda


