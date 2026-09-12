# 📈 Machine Learning: Regression & Classification Notes

## 1. Linear vs. Logistic (The Great Divide)

### Linear Regression (Simple & Multiple)

Used to predict a **continuous** value (e.g., house price).

- **Formula:** y=β0​+β1​x1​+...+βn​xn​

```python
from sklearn.linear_model import LinearRegression
model = LinearRegression().fit(X_train, y_train)
predictions = model.predict(X_test) # Result: 245.5, 102.1...
```
### Logistic Regression

Used to predict a **probability** of a class (e.g., Titanic survival).

- **Formula:** p=1+e−(Linear Eq)1​
    
```python
from sklearn.linear_model import LogisticRegression
model = LogisticRegression().fit(X_train, y_train)
probs = model.predict_proba(X_test) # Result: [0.1, 0.9]
```

---
## 2. Advanced Regression Variations

### Polynomial Regression

Used when the relationship between data points is **curved**, not a straight line.
```python
from sklearn.preprocessing import PolynomialFeatures
poly = PolynomialFeatures(degree=2)
X_poly = poly.fit_transform(X) # Creates X^2 terms
```

### Regularized Regression (Ridge & Lasso)

Used to prevent **Overfitting** by penalizing large coefficients.

- **Ridge (L2):** Shrinks coefficients toward zero (good when most features are useful).
- **Lasso (L1):** Can shrink coefficients to **exactly zero** (performs automatic feature selection).
    
```python
from sklearn.linear_model import Ridge, Lasso
ridge = Ridge(alpha=1.0).fit(X, y)
lasso = Lasso(alpha=0.1).fit(X, y)
```


## Python Code for Logistic Regression

```python
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import accuracy_score, confusion_matrix, classification_report

# 1. Define Features and Target
X = df_train.drop("Survived", axis=1)
y = df_train["Survived"]

# 2. Split into Training and Validation sets (80/20 split)
X_train, X_val, y_train, y_val = train_test_split(X, y, test_size=0.2, random_state=42)

# 3. Feature Scaling (Crucial for Logistic Regression)
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_val_scaled = scaler.transform(X_val)

# 4. Initialize and Train the Model
# max_iter=1000 ensures the algorithm has enough time to converge
logreg = LogisticRegression(max_iter=1000)
logreg.fit(X_train_scaled, y_train)

# 5. Predictions
y_pred = logreg.predict(X_val_scaled)

# 6. Evaluation
print(f"✅ Validation Accuracy: {accuracy_score(y_val, y_pred):.2%}")
print("\n--- Confusion Matrix ---")
print(confusion_matrix(y_val, y_pred))
print("\n--- Classification Report ---")
print(classification_report(y_val, y_pred))
```

### 📝 Note: Feature Scaling

> [!ABSTRACT] **StandardScaler** **Purpose:** Ensures all features contribute equally to the model's result, regardless of their original units.
> 
> **Why for Logistic Regression?** > Logistic Regression relies on "Gradient Descent" or coordinate descent to find the best weights. If features have different scales, the "path" to the best answer becomes very distorted and slow.

### ⚖️ Comparison: When to Scale?

| Model                   | Does it need Scaling? | Why?                                                                         |
| ----------------------- | --------------------- | ---------------------------------------------------------------------------- |
| **Logistic Regression** | **YES**               | Relies on weights; treats larger numbers as more important.                  |
| **KNN**                 | **YES**               | Calculates distance; a large number (Fare) will drown out a small one (Sex). |
| **SVM**                 | **YES**               | Tries to maximize the "gap" between classes.                                 |
| **Decision Trees**      | **NO**                | They just ask "Is Age > 30?" The scale doesn't change the logic.             |
| **Random Forest**       | **NO**                | Same as Decision Trees.                                                      |
