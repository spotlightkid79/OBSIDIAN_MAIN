---
id: "nmr50lpkt6j2u"
parent: null
position_x: 
position_y: 
color: null
---
# StandardScaler_MinMaxScaler_Normalization

**Folder:** [[🧹 02 · Data Manipulation & Cleaning]] · **Topic:** #cleaning

## What it is
Put features on the same scale so distance/gradient-based models behave well.
- **StandardScaler** — mean 0, std 1 (most common)
- **MinMaxScaler** — squeeze to [0, 1]
- **RobustScaler** — uses median/IQR, resistant to [[Outliers]]

## Key idea
Tree models don't need scaling; SVMs, KNN, neural nets, and PCA absolutely do.

## Python
```python
from sklearn.preprocessing import StandardScaler
import numpy as np
X = np.array([[1, 100], [2, 300], [3, 500]])
scaler = StandardScaler().fit(X)
print(scaler.transform(X))

```
- **Standardization (Z-score):** ```python from sklearn.preprocessing import StandardScaler df['scaled'] = StandardScaler().fit_transform(df[['value']])
- **Normalization (Min-Max):** ```python from sklearn.preprocessing import MinMaxScaler df['norm'] = MinMaxScaler().fit_transform(df[['value']])


```python
#https://www.kaggle.com/datasets/rafsunahmad/plane-price-prediction

import pandas as pd
import numpy as np
from sklearn.preprocessing import StandardScaler,MinMaxScaler

df=pd.read_csv('plane.csv')
df.head(3)
df.info()

df=df[["Rcmnd cruise Knots","Stall Knots dirty","Fuel gal/lbs","Eng out rate of climb","Price"]]

df.head(3)
df=df.dropna()
y=df['Price']
x=df.drop("Price",axis=1)

# Y için normalizasyon yapılmaz
# outlier etkisini azaltır
# model performansız artar

ss=StandardScaler()
x2=ss.fit_transform(x)
x2=pd.DataFrame(x2)
x2.head(3)
x2[2].mean()
x2[2].std()

mm=MinMaxScaler()
x3=mm.fit_transform(x)
x3=pd.DataFrame(x3)
x3.head(3)
x3[0].max()
x3[0].min()

# 1994-2024 ---> 0,1 ---> 2000 --> 0.54
# 0-250.000----> 0,1 ---- 120000-> 0.52

mm2=MinMaxScaler(feature_range=(0,10))
x4=mm2.fit_transform(x)
x4=pd.DataFrame(x4)
x4[2].max()
x4[2].min()
```


## 🔗 Related
- [[Outliers]]
- [[Dimensionality_Reduction]]
- [[Clustering]]



#StandardScaler , 
#MinMaxScaler ,
#Normalizasyon
