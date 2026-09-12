






```python
import pandas as pd
import numpy as np
from sklearn.linear_model import LinearRegression
from sklearn.ensemble import RandomForestRegressor
from sklearn.model_selection import train_test_split
#https://www.kaggle.com/datasets/mirichoi0218/insurance

df=pd.read_csv('insurance.csv')
df.head(3)

df=pd.get_dummies(df,columns=["sex","smoker","region"],drop_first=True)
df.head(3)

y=df['charges']
x=df.drop(columns=["charges"])

x_train,x_test,y_train,aa=train_test_split(x,y,random_state=22,train_size=0.7)

lr=LinearRegression()
model=lr.fit(x_train,y_train)
model.score(x_test,y_test)

rf=RandomForestRegressor(n_estimators=200)
model=rf.fit(x_train,y_train)
model.score(x_test,y_test)

model.predict([[31,27.4,0,1,0,1,0,0]])

```