
#Regularization techniques used to prevent **overfitting** by adding a penalty term to the cost function. This helps achieve the perfect **Bias-Variance Tradeoff**.
## 1. Ridge Regression (L2 Regularization)

Ridge regression adds a "penalty" equivalent to the **square of the magnitude** of coefficients.

- **L2 Penalty:** α×∑(coefficients)2
- **Key Characteristics:**
    - **Overfitting Control:** Prevents the model from becoming too complex.
    - **Coefficient Shrinkage:** It shrinks coefficients toward zero, but they **never become exactly zero**.
    - **Feature Retention:** Since coefficients don't hit zero, it keeps all features in the model (no feature selection).
    - **Alpha (α):** The tuning parameter. If α=0, it is a simple Linear Regression. As α increases, the penalty grows and coefficients shrink further.

---
## 2. Lasso Regression (L1 Regularization)

Lasso (Least Absolute Shrinkage and Selection Operator) adds a "penalty" equivalent to the **absolute value** of the magnitude of coefficients.

- **L1 Penalty:** α×∑∣coefficients∣
- **Key Characteristics:**
    - **Feature Selection:** Unlike Ridge, Lasso can shrink coefficients **exactly to zero**.
    - **Sparse Models:** It effectively removes unimportant features, acting as a built-in feature selection tool.
## 🧪 Implementation Example (Ridge)

Using the student scores dataset to see how different α values affect the model's R2 score and coefficients.

```python

# Ridge regresyon overfitting (Aşırı öğrenme durumları için kullanılır)
# Ridge regresyon sayesinde bias ve varyans arasındaki dengeyi sağlauyabiliriz.
# Ridge regresyonda katsayılar üzerinde regülasyon yapılıyor
# ridge regresyonda katsayılar küçülür ama sıfır olmaz. Features öz nitelik azalmaz
# ridge regresyon cezalar karesi ile orantılı
# ridge regresyon l2

# y = a1 * x1 + a2 * x2 +...... + b + alfa * (katsayılartoplamı)**2
# 50 = 40 + 10 + 0
#50 = 20 +10 +20

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression, Ridge

# Load Data
df = pd.read_csv('student_scores.csv')
y = df['Scores']
x = df[['Hours']]

# Simple Linear Regression (Baseline)
lr = LinearRegression()
model = lr.fit(x, y)
print(f"Base LR Score: {model.score(x, y)}")

# Testing different Alpha values for Ridge
alfalar = [1, 10, 20, 100, 200]

print("\n--- Ridge Regression Results ---")
for a in alfalar:
    r = Ridge(alpha=a)
    modelr = r.fit(x, y)
    skor = modelr.score(x, y)
    print(f"Alpha: {a:<4} | Score: {skor:.4f} | Coefficients: {modelr.coef_}")

```

## 📊 Comparison Table

| Feature               | Ridge Regression (L2)         | Lasso Regression (L1)                |
| --------------------- | ----------------------------- | ------------------------------------ |
| **Penalty Term**      | α×(slope)2                    | $\alpha \times                       |
| **Coefficients**      | Shrink towards zero (never 0) | Can shrink exactly to zero           |
| **Feature Selection** | No                            | Yes                                  |
| **Best used when...** | Most variables are useful     | Only a few variables are significant |