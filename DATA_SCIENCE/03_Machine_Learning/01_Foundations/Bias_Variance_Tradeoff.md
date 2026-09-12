# Bias–Variance Tradeoff

**Folder:** [[🧱 Foundations]] · **Topic:** #ml
## What it is
- **High bias** = underfitting (model too simple, misses patterns)
- **High variance** = overfitting (model memorizes training noise)

Total error = bias² + variance + irreducible noise.
## Key idea

Increasing model complexity lowers bias but raises variance. The sweet spot is the lowest **validation** error.

## Python
```python
# Underfit vs overfit polynomial
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression
from sklearn.pipeline import make_pipeline
import numpy as np
X = np.linspace(0, 1, 30).reshape(-1, 1); y = np.sin(2*np.pi*X.ravel()) + 0.1*np.random.randn(30)
for d in [1, 4, 15]:
    m = make_pipeline(PolynomialFeatures(d), LinearRegression()).fit(X, y)
    print(f"degree {d}: R² = {m.score(X, y):.3f}")
```

# 📉 Analyzing Model Fit via `.score()`

In `scikit-learn`, the `.score(x, y)` method calculates the R2 value, which helps identify if the model is well-balanced or suffering from overfitting.
### 🧪 The Workflow

```python
import seaborn as sns
import pandas as pd 
import numpy as np 
from sklearn.linear_model import LinearRegression 
from sklearn.model_selection import train_test_split

df = sns.load_dataset('diamonds')
df.head()
df=df.get_dummies(df,columns=['cut','color','clarity'], drop_first=True)
df.head()

y=[['price']]
x=df.drop('price',axis=1)

x_train,x_test,y_train,y_test = train_test_split(x,y,random_state=19,train_size=0.76)

lm=LinearRegression()
model=lm.fit(x_train,y_train)

model.score(x_test,y_test)
model.score(x_train,y_train)

```

### 🔍 How to Interpret the Difference

|Scenario|Score Relationship|Conclusion|
|---|---|---|
|**Balanced**|`train_score` ≈ `test_score`|**Good Fit:** The model generalizes well to unseen data.|
|**Overfitting**|`train_score` ≫`test_score`|**Overfit:** High variance. The model memorized the noise in training but fails on test data.|
|**Underfitting**|Both scores are low|**Underfit:** High bias. The model is too simple to learn the data pattern.|

## 🔗 Related
- [[Regularization]]
- [[Cross_Validation]]
- [[Classification Model Evaluation]]
