# pandas
```python
import pandas as pd
import numpy as np
array = np.array([1,2,3,4,5])
print(array)
pd.Series(array)
dict = {'new':23,'ghoop':34,'hi':34}
ser = pd.Series(dict)
print(ser)
s1 = pd.Series([1,2,3,4,5],index = [1,2,3,4,5])
s2 = pd.Series([6,7,8,9,10],index = [1,2,3,4,5])
s3 = s1 + s2
print(s3)
s1 = pd.Series([1,2,3,4,5],index = [1,2,3,4,5])
s2 = pd.Series([6,7,8,9,10],index = [1,2,3,4,5])
s3 = s1 / s2
print(s3)
s1 = pd.Series([1,2,3,4,5],index = [1,2,3,4,5])
s2 = pd.Series([6,7,8,9,10],index = [1,2,3,4,5])
s3 = s1 * s2
print(s3)
s1 = pd.Series([1,2,3,4,5],index = [1,2,3,4,5])
s2 = pd.Series([6,7,8,9,10],index = [1,2,3,4,5])
s3 = s1 - s2
print(s3)
print(s1[1:3])
lol = pd.DataFrame ({'Name':['nfdsn','ffajsndkjd','jbfdj'],
               'Age':[23,45,56],
               'Sex':['Male','Female','Female']},
              index = ['no','yes','maybe'])
print(lol)
city = ['Nunubad','jalabad','bosdipur']
lol["city"] = city
print(lol)
print(lol.shape)
del lol["city"]
print(lol)

```


# dataCleaning
```python
import numpy as np
import pandas as pd
data = {
    'A':[10,20,np.nan,40],
    'B':[30,np.nan,np.nan,40],
    'C':[np.nan,20,np.nan,40],
    'D':[40,20,50,40],
    }
df = pd.DataFrame(data)
print(df)
dropped = df.dropna(axis=1)
print(dropped)
dropped = df.dropna()
print(dropped)
filled = df.fillna(0)
print(filled)
df['A']=df['A'].fillna(df['A'].mean())
df['B']=df['B'].fillna(df['B'].mean())
df['C']=df['C'].fillna(df['C'].mean())
print(df)
from sklearn.impute import SimpleImputer
numerical_imputer = SimpleImputer(strategy='mean')
df[['A','B']] = numerical_imputer.fit_transform(df[['A','B']])
print(df)
categoriacal_imputer = SimpleImputer(strategy='most_frequent')
df[['C','D']] = categoriacal_imputer.fit_transform(df[['C','D']])
print(df)
```


