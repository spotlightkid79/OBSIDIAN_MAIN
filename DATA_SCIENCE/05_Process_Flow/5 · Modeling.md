---
id: "nmr50lpkt2c71"
parent: null
position_x: 
position_y: 
color: null
---
# 5 · Modeling

**Folder:** [[🔄 05 · Process Flow]] · **Topic:** #process #ml

## What it is
Train candidate models. Start simple (linear / logistic baseline), then escalate to trees / boosting / nets as needed. Tune hyperparameters via [[Cross_Validation|CV]] + [[Hyperparameter_Tuning]].

## Key idea
A strong baseline tells you whether complexity is justified.

## Python
```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import cross_val_score
from sklearn.datasets import load_breast_cancer
X, y = load_breast_cancer(return_X_y=True)
print(cross_val_score(RandomForestClassifier(random_state=0), X, y, cv=5).mean())
```

## Related
- [[01 Regression]] · [[01 Classification]] · [[Clustering]]
- [[Ensemble_Methods]] · [[Neural_Networks_Intro]]
- next → [[6 · Evaluation]]
