---
id: "nmr50lpkttq1h"
parent: null
position_x: 
position_y: 
color: null
---
# Model Selection — Decision Process

**Folder:** [[🤖 03 · Machine Learning]] · **Topic:** #ml

## What it is
A practical decision process for choosing **which ML model to try first**. There is no single "best" model — the right choice depends on the **task**, the **data**, and the **constraints** (interpretability, latency, training cost).

> Rule of thumb: start simple, get a baseline, then add complexity only if the data justifies it.

## Step 1 — What is the task?

```
Do I have labels?
├── Yes → Supervised
│         ├── Predict a number  → Regression
│         └── Predict a category → Classification
│              (ordered in time? → Time-Series Forecasting)
└── No  → Unsupervised
          ├── Group similar points     → Clustering
          ├── Compress / visualize     → Dimensionality Reduction
          └── Spot rare points         → Anomaly Detection

No data, only a reward signal? → Reinforcement Learning
```

See [[Supervised vs Unsupervised]] for the taxonomy.

## Step 2 — What does the data look like?

| Question | If **yes** → lean toward | If **no** → lean toward |
|---|---|---|
| Small dataset (< 10k rows)? | Linear / tree models | Neural nets, gradient boosting |
| Many features, mostly numeric? | Linear models, SVM | Tree-based |
| Mixed types / missing values? | Tree-based (XGBoost, RF) | Linear (after encoding) |
| Highly non-linear relationships? | Trees, kernels, neural nets | Linear |
| Text / images / audio? | Neural networks (CNN, Transformer) | Classical ML |
| Strong feature interactions? | Tree ensembles, neural nets | Linear |

## Step 3 — What are the constraints?

- **Interpretability required?** → Linear/Logistic Regression, single Decision Tree
- **Low-latency inference?** → Linear models, small trees
- **Limited compute / training budget?** → Linear, Naive Bayes, kNN
- **Maximum accuracy on tabular data?** → Gradient Boosting (XGBoost, LightGBM, CatBoost)
- **Maximum accuracy on unstructured data?** → Deep learning

## Step 4 — Pick a starting model

### Regression → see [[01 Regression]]
1. **Linear Regression** — baseline, interpretable.
2. **Ridge / Lasso** — if many features or multicollinearity (see [[Regularization]]).
3. **Random Forest / Gradient Boosting** — non-linear tabular.
4. **Neural Network** — large data, complex patterns.

### Classification → see [[01 Classification]]
1. **Logistic Regression** — baseline, gives probabilities.
2. **Naive Bayes** — text, very fast.
3. **kNN / SVM** — small/medium datasets, clear margins.
4. **Random Forest / XGBoost** — strong default for tabular.
5. **Neural Network** — images, text, very large data.

### Clustering → see [[Clustering]]
- Known **k**, roughly spherical → **K-Means**
- Unknown k, arbitrary shapes → **DBSCAN**
- Hierarchy matters → **Agglomerative Clustering**

### Dimensionality Reduction → see [[Dimensionality_Reduction]]
- Linear, fast → **PCA**
- Visualization in 2D/3D → **t-SNE**, **UMAP**

## Step 5 — Validate, don't guess
1. **Split** the data — train / validation / test.
2. **Baseline first** — a dumb model (mean, majority class) sets the floor.
3. **Cross-validate** — see [[Cross_Validation]].
4. **Pick a metric** that matches the business cost — see [[Classification Model Evaluation]].
5. **Diagnose errors** — under- or over-fitting? See [[Bias_Variance_Tradeoff]].
6. **Tune** only after a model looks promising — see [[Hyperparameter_Tuning]].

## Key idea
Model selection is a **funnel**, not a lottery: task → data → constraints → candidate set → evaluate → tune. The fanciest model that beats a strong baseline by 0.2% is rarely the right answer in production.

## Python — quick bake-off
```python
from sklearn.datasets import load_breast_cancer
from sklearn.model_selection import cross_val_score
from sklearn.linear_model import LogisticRegression
from sklearn.ensemble import RandomForestClassifier, GradientBoostingClassifier
from sklearn.svm import SVC

X, y = load_breast_cancer(return_X_y=True)

candidates = {
    "logreg": LogisticRegression(max_iter=5000),
    "svm":    SVC(),
    "rf":     RandomForestClassifier(n_estimators=200, random_state=0),
    "gb":     GradientBoostingClassifier(random_state=0),
}

for name, model in candidates.items():
    score = cross_val_score(model, X, y, cv=5, scoring="f1").mean()
    print(f"{name:7s} F1={score:.3f}")
```

## Cheat sheet
- **Tabular, < 100k rows** → start with Logistic/Linear Regression, then Gradient Boosting.
- **Tabular, > 1M rows** → Gradient Boosting or a small neural net.
- **Text** → TF-IDF + Logistic Regression baseline → Transformer if needed.
- **Images** → pretrained CNN / ViT, fine-tune.
- **Time series** → ARIMA / Prophet baseline → boosting on lag features → RNN/Transformer.
- **No labels, exploring** → PCA + K-Means/DBSCAN.

## Related
- [[Supervised vs Unsupervised]]
- [[01 Regression]]
- [[01 Classification]]
- [[Clustering]]
- [[Ensemble_Methods]]
- [[Neural_Networks_Intro]]
- [[Classification Model Evaluation]]
- [[Cross_Validation]]
- [[Bias_Variance_Tradeoff]]
- [[Regularization]]
- [[Hyperparameter_Tuning]]
