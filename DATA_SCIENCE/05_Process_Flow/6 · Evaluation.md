---
id: "nmr50lpkt5liq"
parent: null
position_x: 
position_y: 
color: null
---
# 6 · Evaluation

**Folder:** [[🔄 05 · Process Flow]] · **Topic:** #process

## What it is
Verify the model meets the success metric on held-out data. Inspect errors, fairness, calibration, segment performance. Compare against the baseline.

## Key idea
A model that beats the baseline by 0.2% is not always worth shipping. Consider cost, complexity, and risk.

## Python
```python
from sklearn.metrics import classification_report, roc_auc_score
# y_true, y_pred, y_proba from your held-out test set
# print(classification_report(y_true, y_pred))
# print("AUC:", roc_auc_score(y_true, y_proba))
```

## Related
- [[Classification Model Evaluation]]
- [[Bias_Variance_Tradeoff]]
- next → [[7 · Deployment & Monitoring]]
