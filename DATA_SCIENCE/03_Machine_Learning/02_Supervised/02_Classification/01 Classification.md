# Classification

**Folder:** [[🎯 Supervised Learning]] · **Topic:** #ml

## What it is
Predict a **discrete** label (binary or multi-class). Classics: Logistic Regression, KNN, SVM, Decision Trees, Random Forest, Gradient Boosting, Neural Nets.

## Key idea
Watch class imbalance — accuracy is misleading. Use precision/recall/F1/ROC-AUC ([[Classification Model Evaluation]]).

## Python
```python
from sklearn.datasets import load_breast_cancer
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
X, y = load_breast_cancer(return_X_y=True)
Xtr, Xte, ytr, yte = train_test_split(X, y, random_state=0)
model = RandomForestClassifier(n_estimators=100, random_state=0).fit(Xtr, ytr)
print("acc:", model.score(Xte, yte))
```

## 🔗 Related
- [[Bayes' Theorem]]
- [[Classification Model Evaluation]]
- [[Ensemble_Methods]]
- [[Hyperparameter_Tuning]]
