# Model Evaluation

**Folder:** [[🧱 Foundations]] · **Topic:** #ml

## What it is
Measuring how good a model is — on **held-out** data, not training data.
- Regression: MAE, RMSE, R²
- Classification: Accuracy, Precision, Recall, F1, ROC-AUC, confusion matrix

## Key idea
Choose a metric that reflects the business cost. Recall matters for fraud; precision for spam filters.

## Python
```python
from sklearn.metrics import classification_report, confusion_matrix
y_true = [0, 1, 1, 0, 1, 1, 0]
y_pred = [0, 1, 0, 0, 1, 1, 1]
print(confusion_matrix(y_true, y_pred))
print(classification_report(y_true, y_pred))
```

## Related
- [[01 Classification]]
- [[Cross_Validation]]
- [[Bias_Variance_Tradeoff]]
