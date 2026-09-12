
kategorisel verilerde daha başarılı denebilir

## 🌳 Random Forest Classifier

An ensemble learning method that constructs a multitude of decision trees during training and outputs the mode of the classes for classification. It is particularly effective for handling categorical data and complex datasets.

### Why Random Forest Excels at Categorical Data

- **Natural Splitting:** The tree-based structure handles categorical features by creating logical branches (e.g., "If Color == Blue") rather than relying on mathematical distances.
- **Non-Linearity:** It easily captures complex, non-linear relationships between categories without needing feature scaling.
- **Reduced Overfitting:** While a single **Decision Tree** often overfits categorical noise, Random Forest averages multiple trees to provide a more stable and accurate prediction.
- **Feature Importance:** It automatically identifies which categorical variables have the most predictive power.
### 💡 Obsidian Note Summary

> **Note:** Random Forest is robust for **Categorical Data** because its ensemble nature prevents the high variance (overfitting) typically seen in single decision trees when dealing with complex categories.
### 🛠️ Core Concepts

- **Ensemble Method:** Combines the "wisdom of the crowd" by averaging results from multiple independent trees to improve overall accuracy.
- **Bagging (Bootstrap Aggregating):** Each tree is trained on a random subset of the data, which helps in reducing variance.
- **Robustness:** Significantly less prone to [[Underfitting, Overfitting, Balanced Fitting]] compared to a single [[01 Decision_Trees (Classifier)]] note because individual tree errors tend to cancel out.

🎯 Implementation (Scikit-Learn)
```python
import pandas as pd
import numpy as np
from sklearn.tree import DecisionTreeClassifier,export_graphviz
import graphviz
from sklearn.model_selection import train_test_split

y=df['output']
x=df.drop("output",axis=1)

x_train,x_test,y_train,y_test=train_test_split(x,y,random_state=16,train_size=0.70)

# Train Test Split ile
tree=DecisionTreeClassifier()
model=tree.fit(x_train,y_train)
model.score(x_test,y_test)

model.predict([[31,1,2,130,240,0,0,150,0,2,0,0,2]])

dot=export_graphviz(model,feature_names=x.columns,filled=True)
gorsel=graphviz.Source(dot)
gorsel

```

```python

from sklearn.ensemble import RandomForestClassifier

forest = RandomForectClassifier()
model= forest.fit(x,y)
model.score(x,y)

forest=RandomForestClassifier(n_estimator=400, max_depth=2)
model=forest.fit(x_train,y_train)
model.score(x_test,y_test)

```

### ⚙️ Key Hyperparameters

- `n_estimators`: The number of trees in the forest (e.g., 400); generally, more trees increase performance but require more computation.
- `max_depth`: Limits how deep each individual tree can grow; useful for controlling overfitting.
- `random_state`: Ensures reproducibility of the results.
    
### 🔗 Related Topics

- [[Ensemble_Methods]]
- [[01 Decision_Trees (Classifier)]]
- [[Underfitting, Overfitting, Balanced Fitting]]
- [[Hyperparameter_Tuning]]
- [[Bias_Variance_Tradeoff]]