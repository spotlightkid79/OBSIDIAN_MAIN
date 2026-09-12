# 📊 Model Evaluation Metrics (Regression)

This note covers the most common evaluation metrics used for regression models in Machine Learning.
## 1. Mean Squared Error (MSE)

The average of the squared differences between the predicted and actual values.

- **Formula:**
    MSE=n1​i=1∑n​(yi​−y^​i​)2
- **Key Insight:** Sensitive to **outliers** because errors are squared.
    
**Python Implementation:**

```python
from sklearn.metrics import mean_squared_error

y_true = [3, -0.5, 2, 7]
y_pred = [2.5, 0.0, 2, 8]

mse = mean_squared_error(y_true, y_pred)
print(f"MSE: {mse}")
```

### 1. Eliminating Negative Values

If we simply added up the errors (yi​−y^​i​), positive errors (overestimates) and negative errors (underestimates) would cancel each other out. A model that is wrong by +100 and −100 would look "perfect" with a sum of zero. Squaring ensures every error is a positive number.
### 2. The "Penalty" Effect (Magnifying Large Errors)

Squaring the error gives much more weight to **large outliers**.
- An error of **2** becomes **4**.
- An error of **10** becomes **100**.
    
By using MSE, you are telling the model: _"It is much worse to be off by 10 once than to be off by 2 five times."_ This forces the model to prioritize reducing those big, glaring mistakes.
### 3. Mathematical Smoothness (The Calculus Reason)

This is the most important reason for optimization:

- **The Square Function is Differentiable:** The function f(x)=x2 has a smooth, continuous derivative (2x) everywhere.
- **The Absolute Function is Not:** The function f(x)=∣x∣ has a "V" shape with a sharp corner at zero, where the derivative is undefined.
---
## 2. Root Mean Squared Error (RMSE)

The square root of MSE. It brings the error metric back to the original units of the target variable.

- **Formula:**
    RMSE=MSE![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="400em"%20height="1.08em"%20viewBox="0%200%20400000%201080"%20preserveAspectRatio="xMinYMin%20slice"><path%20d="M95,702c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429c69,-144,104.5,-217.7,106.5,-221l0%20-0c5.3,-9.3,12,-14,20,-14H400000v40H845.2724s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47zM834%2080h400000v40h-400000z"></path></svg>)​
**Python Implementation:**
```python
import numpy as np
from sklearn.metrics import mean_squared_error

rmse = np.sqrt(mean_squared_error(y_true, y_pred))
# Or in newer scikit-learn versions:
# rmse = mean_squared_error(y_true, y_pred, squared=False)
print(f"RMSE: {rmse}")
```

---
## 3. Mean Absolute Error (MAE)

The average of the absolute differences between the predicted and actual values.

- **Formula:**    
    MAE=n1​i=1∑n​∣yi​−y^​i​∣
- **Key Insight:** More **robust** to outliers compared to MSE.
    
**Python Implementation:**

```python
from sklearn.metrics import mean_absolute_error

mae = mean_absolute_error(y_true, y_pred)
print(f"MAE: {mae}")
```

---
## 4. R-Squared (R2)

Known as the **Coefficient of Determination**. It represents the proportion of variance for the dependent variable that's explained by the independent variables.

- **Range:** −∞ to 1.0 (1.0 is a perfect fit).

**Python Implementation:**

```python
from sklearn.metrics import r2_score

r2 = r2_score(y_true, y_pred)
print(f"R2 Score: {r2}")
```

---
### 🚀 Quick Summary Table

| Metric   | Outlier Sensitivity | Unit Match | Best For                                      |
| -------- | ------------------- | ---------- | --------------------------------------------- |
| **MSE**  | Very High           | No (x2)    | Mathematical optimization (Gradient Descent). |
| **RMSE** | High                | Yes (x)    | General performance reporting.                |
| **MAE**  | Low                 | Yes (x)    | Data with many outliers.                      |
| **R²**   | N/A                 | No         | Explaining the model's fit to the data.       |
## LONG METHOD

```python
import numpy as np 
import pandas as pd 
from sklearn.linear_model import LinearRegression 

df = pd.read_csv('insurance.csv')

pd.get_dummies(df,columns=['sex','smoker','region'], drop_first=True)

y=df[['charges']]
x=df.drop('charges', axis=1)

lm = LinearRegression()
model=lm.fit(x,y)

model.score(x,y)

model.predict([[19,26,0,1,1,0,0,1]])

df_hata=pd.DataFrame()
df_hata['y'] =y
y_tahmin = model.predict(x)
df_hata['tahmin'] = y_tahmin
df_hata['error'] = y - y_tahmin


df_hata['squared_error']=df_hata['error']**2 # mean_squared_error
df_hata['abs_error'] = np.abs[df_hata['error']) # mean_absolute_error
da_hata['percent_error'] = np.abs((y-y_tahmin) / y) # mean_absolute_percentage_error

df_hata.mean()

```


``` Python
from sklearn.metrics import mean_squared_error,mean_absolute_error,mean_absolute_percentage_error 

mean_squared_error(y,y_tahmin)
mean_absolute_error(y,y_tahmin)
mean_absolute_percentage_error(y,y_tahmin)

```


## 🔗 Related

- [[01 Regression]]
- [[Linear Algebra]]
- [[Classification Model Evaluation]]
- [[Regularization]]
- [[Bias_Variance_Tradeoff]]
- [[06 Model Evaluation Metrics (Regression)]]