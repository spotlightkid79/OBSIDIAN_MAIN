# Hyperparameter Tuning

**Folder:** [[🧱 Foundations]] · **Topic:** #ml

## What it is
Find the best model settings (learning rate, depth, n_estimators…). Methods: **GridSearchCV** (exhaustive), **RandomizedSearchCV** (random sample), **Bayesian** (Optuna, scikit-optimize).

## Key idea
Always tune inside [[Cross_Validation|CV]] — never against the test set.

## Python
```python
from sklearn.model_selection import GridSearchCV
from sklearn.ensemble import RandomForestClassifier
from sklearn.datasets import load_iris
X, y = load_iris(return_X_y=True)
grid = GridSearchCV(
    RandomForestClassifier(random_state=0),
    {"n_estimators": [50, 100], "max_depth": [3, 5, None]},
    cv=3,
).fit(X, y)
print(grid.best_params_, grid.best_score_)
```

### 🛠️ Hyperparameter Tuning

Hyperparameter tuning is an **external** process where you choose the structural settings of the model _before_ training begins.

- **Goal:** To find the optimal "configuration" or architecture for the model.
- **Controlled by:** The data scientist/developer.
- **Timing:** Set before the actual training process starts.
- **Examples:** The `max_depth` of a Decision Tree, the `learning_rate` of an optimizer, or the number of clusters (k) in K-Means.
- **Analogy:** Choosing the blueprint and engine size for a car before it starts driving.

### ⚖️ Summary Comparison

|Feature|Hyperparameter Tuning|Optimization (Parameters)|
|---|---|---|
|**Level**|Higher-level configuration|Lower-level internal learning|
|**When?**|Before training|During training|
|**Who?**|Set by the user|Learned by the model|
|**Output**|Optimal model settings|Optimal model weights|
## Related
- [[Cross_Validation]]
- [[Regularization]]
- [[Ensemble_Methods]]
