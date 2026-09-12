# 📊 Model Evaluation — Regression Metrics

## Python
```python
from sklearn.metrics import mean_squared_error, mean_absolute_error, mean_absolute_percentage_error
```
---
## 🔹 1. Mean Absolute Error (MAE)

**Definition:**  
MAE measures the average magnitude of errors without considering direction.

## 📐 Formula

$$\text{MAE} = \frac{1}{n}\sum_{i=1}^{n}\left|y_i - \hat{y}_i\right|$$

**Key Characteristic:**  
- Not sensitive to outliers  
- Treats all errors equally  

**Best For:**  
- When you want a simple, interpretable average error  

---
## 🔹 2. Mean Squared Error (MSE)

**Definition:**  
MSE measures the average of squared errors.

## 📐 Formula
$$\text{MSE} = \frac{1}{n}\sum_{i=1}^{n}\left(y_i - \hat{y}_i\right)^2$$

**Key Characteristic:**  
- Heavily penalizes large errors (outliers)  
- Smooth and differentiable (useful for optimization)

**Best For:**  
- Training models (loss functions)  
- Situations where large errors are costly  

---
## 🔹 3. Root Mean Squared Error (RMSE)

**Definition:**  
RMSE is the square root of MSE.

## 📐 Formula
$$\text{RMSE} = \sqrt{\frac{1}{n}\sum_{i=1}^{n}\left(y_i - \hat{y}_i\right)^2}$$

**Key Characteristic:**  
- Same units as the target variable  
- Still penalizes large errors  

**Best For:**  
- Reporting model performance in real-world units  

---
## 🔹 4. Mean Absolute Percentage Error (MAPE)

**Definition:**  
MAPE expresses error as a percentage.

## 📐 Formula
$$\text{MAPE} = \frac{100\%}{n}\sum_{i=1}^{n}\left|\frac{y_i - \hat{y}_i}{y_i}\right|$$

**Key Characteristic:**  
- Scale-independent (percentage-based)  
- Sensitive when actual values are near zero  

**Best For:**  
- Business reporting  
- Forecasting and stakeholder communication  

---
## 📊 Comparison Table

| Metric | Sensitive to Outliers? | Units | Main Use Case |
|--------|------------------------|-------|--------------|
| MAE | ❌ No | Original | Stable, general performance |
| MSE | ✅ High | Squared | Optimization / loss function |
| RMSE | ✅ Yes | Original | Standard reporting |
| MAPE | ⚠️ Yes (small values) | % | Business interpretation |

---
## 🧠 Quick Summary
- **MAE** → simple, robust  
- **MSE** → punishes big errors  
- **RMSE** → interpretable + punishes big errors  
- **MAPE** → percentage-based, easy to explain  

