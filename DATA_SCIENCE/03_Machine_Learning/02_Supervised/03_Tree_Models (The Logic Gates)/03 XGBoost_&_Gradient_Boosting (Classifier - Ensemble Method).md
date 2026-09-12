






```python
from IPython.display import display, Image

image_url = "https://miro.medium.com/v2/resize:fit:953/1*wpVgt07J_TeH3jEdc3A50g.png"

display(Image(url=image_url))

import pandas as pd
import numpy as np
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
import xgboost as xgb
from sklearn.model_selection import train_test_split

df=pd.read_csv("heart.csv")
df.head(3)

y=df['output']
x=df.drop(columns=["output"])

x_train,x_test,y_train,y_test=train_test_split(x,y,random_state=42,train_size=0.7)

dt=DecisionTreeClassifier()
model=dt.fit(x,y)
model.score(x,y)

dt=DecisionTreeClassifier()
model=dt.fit(x_train,y_train)
model.score(x_test,y_test)

rf=RandomForestClassifier(n_estimators=200)
model=rf.fit(x_train,y_train)
model.score(x_test,y_test)

rf=xgb.XGBClassifier()
model=rf.fit(x_train,y_train)
model.score(x_test,y_test)

df.shape

insan=df.sample().drop("output",axis=1).values

model.predict(insan)

```