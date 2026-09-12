## 1. Regression Evaluation (Predicting Numbers)

_Used for: Simple/Multiple Linear, Polynomial, Ridge, Lasso._

| Metric                                      | What it Tells You                        | Best Used When...                                                                |
| ------------------------------------------- | ---------------------------------------- | -------------------------------------------------------------------------------- |
| **MAE** (Mean Absolute Error)               | The average "distance" of your error.    | You want an error metric in the same units as your target (e.g., dollars).       |
| **MSE** (Mean Squared Error)                | Penalizes large errors heavily.          | You want to avoid big "misses" at all costs.                                     |
| **RMSE** (Root Mean Squared Error)          | The standard deviation of the residuals. | This is the industry standard for reporting regression accuracy.                 |
| **R² Score** (Coefficient of Determination) | How much of the variance is explained.   | You want to know how much "better" your model is than just guessing the average. |

---
## 2. Classification Evaluation (Predicting Labels)

_Used for: Logistic Regression, KNN, SVM, Naive Bayes, Decision Trees (Classifier)._

|Metric|What it Tells You|Best Used When...|
|---|---|---|
|**Accuracy**|Overall % of correct guesses.|Classes are balanced (e.g., 50% survived, 50% died).|
|**Confusion Matrix**|The raw count of TN, FP, FN, TP.|You need to see exactly _where_ the model is getting confused.|
|**Precision**|Accuracy of positive predictions.|The cost of a **False Positive** is high (e.g., Spam filters).|
|**Recall (Sensitivity)**|Ability to find all positive cases.|The cost of a **False Negative** is high (e.g., Cancer detection).|
|**F1-Score**|Balance of Precision & Recall.|You have imbalanced classes (e.g., 90% died, 10% survived).|
|**ROC-AUC**|Model's ability to distinguish classes.|You want to check how good the model is at "ranking" probabilities.|

---
## 🌳 3. Tree-Based Specifics

Since tree models (Random Forest, XGBoost) can do both, the metric depends on the **Task**:

- If doing **Classification** → Use Classification metrics (F1, Accuracy).    
- If doing **Regression** → Use Regression metrics (RMSE, R²).
---
## 📝 Note: Metric Selection Matrix

> [!TIP] **Cheat Sheet**
> 
> - **Predicting Prices/Values?** → Go to `01_Regression` evaluation → Use **RMSE**.
>     
> - **Predicting Categories (Titanic)?** → Go to `02_Classification` evaluation → Use **Confusion Matrix & F1-Score**.
>     

### Python Code for your "Evaluation Master" Note

Python

```
from sklearn import metrics

# FOR REGRESSION
print("MAE:", metrics.mean_absolute_error(y_val, y_pred))
print("RMSE:", np.sqrt(metrics.mean_squared_error(y_val, y_pred)))
print("R2 Score:", metrics.r2_score(y_val, y_pred))

# FOR CLASSIFICATION
print("Accuracy:", metrics.accuracy_score(y_val, y_pred))
print("Confusion Matrix:\n", metrics.confusion_matrix(y_val, y_pred))
print("Classification Report:\n", metrics.classification_report(y_val, y_pred))
```

---

**Analyst Strategy:** In your **Titanic project**, because the number of people who died is higher than those who survived, **Accuracy** can be misleading. I recommend looking at your **F1-Score** to make sure you aren't just getting a high score by predicting "Died" for everyone!

Should we look at your **F1-Score** from your Logistic Regression results?


| Task Type          | Evaluation Tool      | What it measures                              |
| ------------------ | -------------------- | --------------------------------------------- |
| **Regression**     | **RMSE / R²**        | How far away the predicted number was.        |
| **Classification** | **Confusion Matrix** | How many times the label was right vs. wrong. |

