# series and dataframe
Series is a 1D labeled array
A series is essentially a column of data with a label or name, and an associated index that is used to access the data

```python
import pandas as pd
# creating series in pandas
data = [1,2,3,4,5]
series = pd.Series(data,index = ['A','B','C','D','E'])
print(series)
```

DataFrame is a 2D labeled data structure
A DataFrame is essentially a table where each column is a series and each row has a lebel or index
```python
# creating dataframe in pandas
data = {'Name':['Vidhi','Sonakshi','Devdutt','Hiya','Rohan'],
        'Age':[20,34,22,21,18],
        'color':['Blue','Red','Green','White','Pink']}
df = pd.DataFrame(data)
print(df)
```
# data transformation
## Grouping
Group-by: it is use to group your data based on one or more columns.
This allows you to aggregate functions such as mean, sum or count to your data, based on the groups
```python
data = {'Name':['Vidhi','Sonakshi','Devdutt','Rohan'],
        'Age':[20,34,22,18],
        'Country':['India','Brazil','Nepal','Australia']}
df = pd.DataFrame(data)
groupeddata = df.groupby(['Country'])
print(groupeddata['Age'].mean())
```
## merging
Merging and joining dataframes: it is used to combine data from multiple dataframes into single dataframe
```python
data1 = {'Name':['Vidhi','Sonakshi','Devdutt','Hiya','Rohan'],
         'Age':[20,34,22,21,18]}

data2 = {'Name':['Vidhi','Sonakshi','Devdutt','Hiya','Rohan'],
         'Color':['Blue','Red','Green','White','Pink']}
df1 = pd.DataFrame(data1)
df2 = pd.DataFrame(data2)
mergedata = pd.merge(df1,df2,on='Name')
print(mergedata)
```
## concatenation
It is mainly used to reorganise data.
It allows you to combine dataframes vertically or horizontally, while reshaping allows you to rearrange the data in your dataframe into different shapes.
```python
data1 = {'Name':['Vidhi','Sonakshi'],
         'Age':[20,34]}

data2 = {'Name':['Devdutt','Rohan'],
         'Age':[22,21]}
df1 = pd.DataFrame(data1)
df2 = pd.DataFrame(data2)
Concatenateddata = pd.concat([df1,df2],axis = 0)
print(Concatenateddata)
```
# sorting, filtering and mapping of data
```python
import pandas as pd
data = {'Name':['Vidhi','Devdutt','Hiya','Rohan'],
        'English':[40,42,42,34],
        'Maths':[45,40,42,37],
        'Hindi':[37,40,37,45]}
df = pd.DataFrame(data, index = [1,2,3,4])
print(df)
```
## sort
Sorting is a process or arange data in particular order
```python
# sorting data
engdatasort = df.sort_values(by = ['English'], ascending = False)
print(engdatasort)
print('\n')
# sorting multiple columns
data_s = df.sort_values(by = ['English','Maths'], ascending = [True,False])
print(data_s)
```
## Filtering
Filtering is a process of selecting a subset of data based on certain conditions
```python
# filtering data
# boolean
filterddata = df[df['Maths']>42]
print(filterddata)
print('\n')
# passing multiple conditions
filterddata = df[(df['Maths']>40)&(df[Hindi]>35)]
print(filterddata)
```
## mapping
Mapping data is the process of replacing one value with another value
```python
mapped = {'Vidhi':2,'Hiya':1,'Devdutta':2,'Rohan':0}
df['Proficiency']= = df['Name'].map(mapped)
print(df)
```
Reshaping data is process of transforming data from one form to another

# Indexing and slicing
```python
import pandas as pd
# indexing
data = {'Name':['Vidhi','Hiya','Devdutt','Rohan'],
        'Age':[20,21,23,18],
        'Country':['India','Brazil','Nepal','Australia']}
df.DataFrame(data)
print(df)
print(df['Age'])
```
----
Index in pandas allows you to extract specific values or groups of values from a series or dataframe
```python
# df.loc df.iloc
# row_indexer, col_indexer
print(df.loc[0,'Name'])
print(df.iloc[0.0])
```
---
Slicing in pandas allows you to extract a portion of the data in your series or dataframe
```python
print(df[1:3])
#[start:stop, col_indexer]
print(df.loc[1:3,['Name','Country']])
```
# data cleaning
Data cleaning and prepration are essential steps in data analysis pipeline.
The process of data cleaning identifyingn and handling issues within dataset that could cause inaccurate and baised analysis result.
This process involves halndling missing values, removing duplicate, scaling data, encoding categorical data
```python
import pandas as pd
data = {'A':[1,2,2,3,5,9],
        'B':[4,5,5,7,18,0]}
df = pd.DataFrame(data)
print(df)
```
---
```python
print(df.duplicated())
df1 = df.drop_duplicates()
print(df1)
q = df['A'].quantile(0.99)
print(q)
df['A'] = df['A'].clip(lower = None, upper = q)
print(df)
```
---
```python
# Handling missing values
import numpy as np
data = {'A':[1,2,3,np.nan,np.nan],
        'B':[5,np.nan,6,7,np.nan]}
df = pf.DataFrame(data)
print(df)

print(df.isna())

df['A'] = df['A'].fillna(df['A'].mean())
df['B'] = df['B'].fillna(df['B'].mean())
```
---
```python
# data normalization and scaling
max_value = df.max()
min_value = df.min()
print(max_value)
print(min_value)
```
---
```python
#encoding of categorical data
data = {'A':['Red','Blue','Yellow','Pink','White','Purple'],
        'B':[4,5,5,7,18,0]}
df = pd.DataFrame(data)
print(df)

df = pd.get_dummies(df, columns = ['A'])
print(df)

df['A'] = df['A'].replace({'Red':0,'Blue':1,'Yellow':18,'Pink':37,'White':3,'Purple':4})
print(df)
```
# data exploration
Data exploration and visulization are two critical component of data analysis.
They help to understand the underlying pattern of the data.
which in-turn can lead to meaningful insights and decisions.
```python
import pandas as pd
df = pd.read_csv('https://.....iris.csv')
# understanding descriptive stats
df.describe()
```
---
```python
# integrating with other library
import numpy as np
import matlotlib.pyplot as plt
import seaborn as sb
import plotly.express as px
np_array = df.values
print(np_array)
df.plot()
plt.show()
sb.scatterplot(data = df, x = "patel_length", y = "patel_width")
plt.show()
df.hist(column = "patel_legth")
plt.show()
df.boxplot(column = ['petal_length','petal_width','sepal_length','sepal_width'])
plt.show()
figscatter = px.scatter(df, x = 'sepal_width', y = 'sepal_length')
figscatter.show()
```
----
```python
# correlation and covariance
df.corr()
df.cov()
```
# Time
## time series analysis
Time series analysis is a statistical technique that can be used to extract meaningful insights from time series data.
It is commonly used in various feilds such as finance, weather-forcasting and many others
```python
import pandas as pd
import datetime as dt
#date time
date = pd.datetime(year,month,date,hour,minute,seconds)
date = pd.datetime(2022, 04, 21, 13, 54, 19)

# date time index
df = pd.dataframe({'A':[1,2,3]}, index = pd.DatetimeIndex(['2022-01-03','2023-05-17','2020-09-23']))

# shift data
shifted_data = df.shift(periods = 2)
print(shifted_data)

#lagged
df['lagged'] = df['A'].shift(periods = 1)
print(df)

#resampling
resampledata = df.resample('M').sum()
print(resampledata)

```
## time decomposition
Time series data can be decomposed into its trend, seasonal, and residual components
```python
import pandas as pd
import numpy as np

dates = pd.date_range(start = '2020-01-01', end = '2022-03-01')
values = np.random.randint(low = 1, high = 100, size = len(dates))
df = pd.DataFrame({'date':dates, 'value': values})

df = df.set_index('date')
from statsmodels.tsa.seasonal import seasonal_decompose
decomposition = seasonal_decompose(df['value'], period = 7)

df['trend'] = decomposition.trend
df['seasonal'] = decomposition.seasonal
df['residual'] = decomposition.resid

print(df)
```


## Time series forcasting
#### ARIMA
ARIMA models are used for time series data that have a seasonal component

```python
dates =  pd.date_range(start = '2020-01-01', end = '2022-03-31')
values = np.random.randint(low = 1, high = 100, size = len(dates))
df = pd.DataFrame({'date':dates, 'value': values})

df = df.set_index('date')
from statsmodels.tsa.arima.model import ARIMA

# fiting an ARIMA (1, 1, 1) model to the time series data
model = ARIMA(df['value'], order = (1, 1, 1))
model_fit = model.fit()

# making a 7 day forcast
forcast = model_fit.forecast(steps = 7)
print(forcast)
```

#### SARIMA
SARIMA models are used for time series data that does not  have a seasonal component
```python
dates =  pd.date_range(start = '2020-01-01', end = '2022-03-31')
values = np.random.randint(low = 1, high = 100, size = len(dates))
df = pd.DataFrame({'date':dates, 'value': values})

df = df.set_index('date')
from statsmodels.tsa.statespace.sarimax import SARIMAX

# fiting an ARIMA (1, 1, 1) model to the time series data
model = SARIMAX(df['value'], order = (1, 1, 1), seasonal_order = (1, 1, 1, 7))
model_fit = model.fit()

# making a 7 day forcast
forcast = model_fit.forecast(steps = 7)
print(forcast)
```
