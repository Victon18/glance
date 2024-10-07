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


# preprocessing
It refers to the steps and  techniques used to prepare raw  data for modelling
It is a critical as the quality and suitability of the data directly impact the effectiveness of the models built upon it.

## imputation
Data imputation is a technique used to handle missing values in a dataset
Missing values can arise from various reasons such as errors in data collection, corruption, or simply the unavailability of information.
It is crucial because many machine learning algorithms cannot work with datasets that contain missing values.

### dataCleaning
```python
import numpy as np
import pandas as pd
#---------------
# identifying missing data
#----------------
data = {
    'A':[10,20,np.nan,40],
    'B':[30,np.nan,np.nan,40],
    'C':[np.nan,20,np.nan,40],
    'D':[40,20,50,40],
    }
df = pd.DataFrame(data)
print(df)
#----------------------
# removing missing values
#-----------------------

# Removing columns with missing values
dropped = df.dropna(axis=1)
print(dropped)

# Removing rows with missing values
dropped = df.dropna()
print(dropped)

#-----------------------
# Simple Imputing
#----------------------

# Imputing with a Constant Value
filled = df.fillna(0)
print(filled)

#Filling missing numerical values with the mean, median, or mode of the column
df['A']=df['A'].fillna(df['A'].mean())
df['B']=df['B'].fillna(df['B'].mean())
df['C']=df['C'].fillna(df['C'].mean())
print(df)

#--------------------
# Advance imputation
#-------------------

#  Imputing numerical columns with mean
from sklearn.impute import SimpleImputer
numerical_imputer = SimpleImputer(strategy='mean')
df[['A','B']] = numerical_imputer.fit_transform(df[['A','B']])
print(df)

# Imputing categorical columns with most frequent (mode)
categoriacal_imputer = SimpleImputer(strategy='most_frequent')
df[['C','D']] = categoriacal_imputer.fit_transform(df[['C','D']])
print(df)

# IterativeImputer
#models each feature with missing values as a function of other features and uses that estimate for imputation.

from sklearn.experimental import enable_iterative_imputer
from sklearn.impute import IterativeImputer
iterative_imputer = IterativeImputer()
df[['A', 'B']] = iterative_imputer.fit_transform(df[['A', 'B']])
```
# transformation
- It refers to the process of converting raw data into a format that is suitable and optimal for modeling
- aims to improve the performance of machine learning algorithms by making the data more understandable, normalized, and aligned.

types of data transformation

## normalization
- refers to the process of adjusting the values of numerical features in a dataset to a common scale,
- typically between 0 and 1, without distorting differences in the ranges of values
- algorithms that rely on the distance between data points, such as k-nearest neighbors (KNN) or support vector machines (SVM),
- algorithms that use gradient descent for optimization, such as neural networks and logistic regression.
- This is useful when the features have different units or scales.

$$\large
X_{new}  = \frac{X-X_{min}}{X_{max}-X_{min}}
$$

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
- Standardization, also known as Z-score normalization,
- It is used in to transform the features of a dataset such that they have a mean of zero and a standard deviation of one.
- useful for algorithms that assume the data is normally distributed, such as linear regression, logistic regression, and k nearing neighbouring.
- This is useful when the features have different scales but are normally distributed.

$$\large
X^{i}(std.) = \frac{x^{i}-\mu_{x}}{\sigma_{x}}
$$
```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
df_standardized = pd.DataFrame(scaler.fit_transform(df),columns = df.columns)
df_standardized
```
## feature scaling
- It is a method used to normalize the range of independent variables or features in a dataset.
- It is essential to ensure that features contribute equally to the analysis,
- For algorithms that rely on distance calculations or gradient-based optimizations.

## splititng
- It ensures that we can evaluate our model's performance on unseen data.
- Feature scaling is crucial when features have different scales, as it helps in improving the performance and convergence speed of many machine learning algorithms.
- Splitting the dataset typically involves dividing it into two or three sets:
    - Training Set: Used to train the model.
    - Test Set: Used to evaluate the model.
    - Validation Set: (Optional) Used to tune the model parameters and validate the performance during training.

```python
from sklearn.model_selection import train_test_split
# Import train_test_split from the correct module
data = {'Feature1':[10,20,30,40,50],'Feature2':[100,200,300,400,500],'target': [1,0,1,0,1]}
df = pd.DataFrame(data)
x = df[['Feature1','Feature2']] # features
y = df['target'] # target
y_train,x_test,y_train,y_test = train_test_split(x,y,test_size=0.2,random_state=42)
print(X_test)
print (Y_test)
```
# Dimensionality Reduction
- It involves reducing the number of input variables (features) in a dataset.
- This technique helps in simplifying models, reducing overfitting, and improving the computational efficiency of algorithms.

# Data Augmentation
- It is a technique used to increase the amount and diversity of data available for training machine learning models without actually collecting new data.
- This is useful in situations where data is limited, as it can help improve the robustness and performance of models by providing more varied training examples.
