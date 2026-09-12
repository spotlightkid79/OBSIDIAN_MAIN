
## 🔹 1. Simple Linear Regression

**Condition:**

- Only **1 independent variable (feature)**

**Equation:**

y=β0+β1x+ϵy=β0​+β1​x+ϵ

**Explanation:**
 
- **y** → dependent variable #target
- **x** → independent variable #feature
- **β₀ (intercept)** → starting point of the line #intercept
- **β₁ (coefficient)** → effect of x on y #coefficient
- **ε (error)** → difference between predicted and actual values #error

👉 In simple terms:  
We try to draw the best straight line to predict **y from x**.

## Python
```python
from sklearn.linear_model import LinearRegression
import pandas as pd

# create model
model = LinearRegression()

# train (fit)
model.fit(x, y)

# prediction
y_pred = model.predict(x)

# evaluation
model.score(x, y)

# parameters
model.coef_      # coefficient (β1)
model.intercept_ # intercept (β0)

```
-----

## 🔹 2. Multiple Linear Regression

**Condition:**

- **2 or more independent variables**

**Equation:**

y=β0+β1x1+β2x2+⋯+βnxn+ϵy=β0​+β1​x1​+β2​x2​+⋯+βn​xn​+ϵ

**Explanation:**

- Uses **multiple features** to predict one output
- Each feature has its own coefficient
- More realistic for real-world problems

👉 Example: predicting car price using:

- year
- mileage
- engine size
- horsepower
- etc.

## Python
```python
from sklearn.linear_model import LinearRegression
import pandas as pd
from sklearn.model_selection import train_test_split 

# convert categorical variables to numeric
df = pd.get_dummies(df, columns=['kasa', 'vites', 'yakit'], drop_first=True)

# define variables
y = df['fiyat']
x = df.drop("fiyat", axis=1)

# create and train model
model = LinearRegression()
model.fit(x, y)

# prediction (example input)
model.predict([[2017, 30000, 1.6, 110, 1, 2600, 0, 1]])

# model performance
model.score(x, y)
```
------
## 🔹 Train-Test Split

**Purpose:**  
- To split data into **training** and **testing** sets  
- Helps evaluate how well the model performs on **unseen data**

```python
..............

x_train,x_test,y_train,y_test = train_test_split(x,y,train_size=0.70,random_state=42) # test_size can be assinged too

lm = LinearRegression()
model=lm.fit(x_train,y_train)
model.score(x_test,y_test)

model.predict([[2016,30000,1,0,90,5,0,1,1]])

```
#train_test_split

## 🧠 Explanation

- `x` → features (independent variables)
- `y` → target (dependent variable)
- `x_train` → data used to train the model
- `y_train` → labels for training
- `x_test` → unseen data for testing
- `y_test` → true values for testing

## ⚡ Parameters

- `train_size=0.70` → 70% training, 30% testing
- `test_size` → alternative way to define split
- `random_state=42` → ensures same split every run (reproducibility)

## 🎯 Why It Matters

- Prevents **overfitting**
- Tests real-world performance
- Makes evaluation more reliable

--------

| Feature               | Simple Linear Regression | Multiple Linear Regression |
| --------------------- | ------------------------ | -------------------------- |
| Number of x variables | 1                        | 2 or more                  |
| Complexity            | Simple                   | More complex               |
| Use case              | Basic relationships      | Real-world problems        |

| **Type**                       | **Condition**                | **Equation**                                                          |
| ------------------------------ | ---------------------------- | --------------------------------------------------------------------- |
| **Simple Linear Regression**   | `x` has only **1** column    | $y = \beta_0 + \beta_1x_1 + \epsilon$                                 |
| **Multiple Linear Regression** | `x` has **2 or more**columns | $y = \beta_0 + \beta_1x_1 + \beta_2x_2 + ... + \beta_nx_n + \epsilon$ |
