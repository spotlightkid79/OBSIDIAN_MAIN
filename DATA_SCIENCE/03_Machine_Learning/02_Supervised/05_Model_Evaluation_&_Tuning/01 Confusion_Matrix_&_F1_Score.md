# 📊 Confusion Matrix

## 1. Definition

A table used to evaluate the performance of a **Classification** model. It compares the **Actual** labels versus the **Predicted**labels.

- **True Positive (TP):** Predicted Survived, actually Survived. 
- **True Negative (TN):** Predicted Died, actually Died.
- **False Positive (FP):** Predicted Survived, actually **Died** (Type I Error).
- **False Negative (FN):** Predicted Died, actually **Survived** (Type II Error).
    
---
## 2. Metrics Calculation

The matrix is the "source code" for these three vital metrics:

> [!MATH]
> 
> - **Accuracy** = TotalTP+TN​
>     
> - **Precision** = TP+FPTP​ (Quality: "When I say they survived, am I right?")
>     
> - **Recall** = TP+FNTP​ (Quantity: "Did I find all the survivors?")
>     

---
## 3. Python Implementation

```python
from sklearn.metrics import confusion_matrix, classification_report
import seaborn as sns

# Generate the matrix
cm = confusion_matrix(y_val, y_pred)

# Visualize it
sns.heatmap(cm, annot=True, fmt='d', cmap='Blues')
```

### ⚖️ Regression vs. Classification Evaluation

Since you have a comparison table at the end of your Regression notes, add this small one to your **Confusion Matrix**note:

| Task Type          | Evaluation Tool      | What it measures                              |
| ------------------ | -------------------- | --------------------------------------------- |
| **Regression**     | **RMSE / R²**        | How far away the predicted number was.        |
| **Classification** | **Confusion Matrix** | How many times the label was right vs. wrong. |


















## Related

- [[02 Logistic Regression]]
- [[Regression Comparison]]






