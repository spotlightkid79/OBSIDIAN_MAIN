
## 🌲 Decision Tree Classifier

A supervised learning algorithm that maps out all possible decision paths in a flowchart-like structure to predict categorical outcomes.
### 🛠️ Core Concepts

- **Root Node:** The starting decision point representing the entire dataset.
- **Branches:** Connect nodes based on specific feature values or outcomes.
- **Leaf Nodes:** Terminal nodes that represent the final predicted class (e.g., "Fit" or "Unfit").
- **Entropy & Gini:** Mathematical measures used at each split to determine the "purity" of the data.
- **Information Gain:** The reduction in entropy achieved by splitting on a specific feature.
### 🎯 When to Use Decision Trees

You should prioritize a single Decision Tree in these specific scenarios:

- **Interpretability is Vital:** When you need a "White Box" model where every decision is transparent and easy for stakeholders to trace.
- **Categorical Data:** They naturally handle non-numeric, categorical features without requiring extensive preprocessing.
- **Non-Parametric Nature:** When you make no assumptions about the underlying distribution of the data.
- **Fast Prediction:** While training can be complex, making a prediction with a single tree is extremely fast.
- **Limited Computation:** When you lack the hardware resources to run complex ensemble models like XGBoost.

## ⚖️ Model Comparisons

Use this table to quickly distinguish Decision Trees from other common models:

| Feature               | **Decision Tree**      | **Random Forest**         | **Logistic Regression** | **SVM**                        |
| --------------------- | ---------------------- | ------------------------- | ----------------------- | ------------------------------ |
| **Logic Type**        | Non-linear rules       | Ensemble (Multiple trees) | Linear (Log-odds)       | Linear/Non-linear (Hyperplane) |
| **Interpretability**  | **Highest**(Flowchart) | Low (Black box)           | High (Coefficients)     | Low                            |
| **Overfitting Risk**  | **High**               | Low (Robust)              | Low                     | Moderate                       |
| **Data Requirements** | Small to Medium        | Medium to Large           | Smaller, clean data     | High-dimensional data          |
| **Best For**          | Explainable rules      | Maximum accuracy          | Simple, linear patterns | Complex, high-dim spaces       |
gini katsayısı 
ve 
entropi 
bunları araştır çalış 

overfitting e meyilli bir model, açıkla neden böyle 

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


### 🔗 Related

- [[Hyperparameter_Tuning]]
- [[Bias_Variance_Tradeoff]]
- [[02 Random_Forest (Classifier - Ensamble Method)]]
- [[03 XGBoost_&_Gradient_Boosting (Classifier - Ensemble Method)]]
- [[02 Logistic Regression]]
- [[Feature Engineering]]    