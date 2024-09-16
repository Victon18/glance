# Prepoccessing
x and y plane

## normalization
```python
from sklearn.preprocessing import MinMaxScaler
from sklearn.model_selection import train_test_split
import pandas as pd
data = {'Feature1':[500,250,100,-250,-500,120],'Feature2':[100,200,300,400,500,600],}
df = pd.DataFrame(data)
scaler = MinMaxScaler()
df_normalized = pd.DataFrame(scaler.fit_transform(df),columns = df.columns)
#df_normalized.columns = columns
df_normalized
```
## standardisation
```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
df_standardized = pd.DataFrame(scaler.fit_transform(df),columns = df.columns)
df_standardized
```

## splititng
```python
from sklearn.model_selection import train_test_split
# Import train_test_split from the correct module
data = {'Feature1':[10,20,30,40,50],'Feature2':[100,200,300,400,500],'target': [1,0,1,0,1]}
df = pd.DataFrame(data)
x = df[['Feature1','Feature2']]
y = df['target']
y_train,x_test,y_train,y_test = train_test_split(x,y,test_size=0.2,random_state=42)
print(X_test)
```
# linear regression
forcasting and learning theory

Liner and Logistic


