# forcasting and learning theory

Forecasting is the process of making predictions about future events based on historical data and analysis.
Applications
- Estimating economic indicators such as GDP growth.
-  Predicting disease progression or patient outcomes based on patient data.
-  Analyzing the impact of advertising expenditure on sales.
-  Forecasting demand for inventory management.
-  Modeling pollution levels based on various factors.
-  Predict students' academic performance based on their previous scores, attendance, and other factors.
- Forecast the success rate of recruitment drives based on historical data Etc.

# linear regression

Linear Regression is a supervised learning algorithm in machine learning,
the goal is to predict a continuous output variable based on one or more input variables
we do so by finding the bestfitting linear equation to describe the relationship between the input variables (features)and the output variable (response variable).

- Relationship between Input and Output Variable
---
- positive
- negative

## simple linear regression

Simple linear regression models is the relationship between two variables by fitting a linear equation to observed data.
The linear equation can be written as:

$$\LARGE
y = mx + b
$$

- y is the dependent variable.
- x is the independent variable.
- b is the y-intercept.
- m is the slope of the regression line.

we find the best-fitting line through the data points that minimizes the sum of squared residuals (errors).
This method is called Ordinary Least Squares (OLS)

## multiple linear regression

Multiple linear regression models the relationship between two or more independent variables and a  dependent variable
by fitting a linear equation to the observed data

$$
y=b+m1x1+m2x2+….....+mn\times x^{n}
$$

Where:
•y is the dependent variable.
•x1,x2,…,…,xn are the independent variables.
•b is the y-intercept.
•m1,m2,…......mn are the coefficients.

The goal is to find the best-fitting plane (or hyperplane) that minimizes the sum of squared residuals.

## Ordinary Least Square (OLS) Regression

To find the best-fitting line in a linear regression model, we use a process called “ordinary least squares (OLS) regression”.
This process involves calculating the sum of the squared differences between the predicted values and the actual values for each data point
and then finding the line that minimizes this sum of squared errors.

to achieve best fit line
---
The best-fitting line is found by minimizing the residual sum of squares (RSS),
which is the sum of the squared differences between the predicted values and the actual values.
This is achieved by adjusting the values of the intercept and slope coefficients, also known as c and m, respectively.

Loss functions
---

$$\Large
\begin{align}
E&=\frac{1}{n}\sum_{i=0}^{n}(y_{i}-\overline{y_{i}})^{2}\\
E&=\frac{1}{n}\sum_{i=0}^{n}(y_{i}-(mx_{i}+c))^{2}
\end{align}
$$

# gradient_descent

Gradient descent is an iterative optimization algorithm to find the minimum of a Loss function.

1. step 1
---
Initially let m = 0 and c = 0.
Let L be our learning rate.  This controls how much the value of m changes with each step.
L could be a small value like 0.0001 for good accuracy.

---
2. step 2
---
Calculate the partial derivative of the loss function with respect to m,
and plug in the current values of x, y, m and c in it to obtain the derivative value D

---
3. step 3
---
Now we update the current value of m and using equations

---
4. step 4
---
We repeat this process until our loss function is a very small value or ideally 0 (which means 0 error or 100% accuracy).
The value of m and c that we are left with now will be the optimum values.

---

$$\large
\begin{align}
&\text{partial derivative wrt d}\\
D_{m} &= \frac{1}{n}\sum_{i=0}^{n}2(y_{i}-(mx_{i}+c))(-x_{i})\\
&\text{partial derivative wrt c}\\
D_{c} &= \frac{-2}{n}\sum_{i=0}^{n}2(y_{i}-\overline{y_{i}})\\
&\text{update current values of m and c from equations}\\
m &= m-L\times D_{m}\\
c &= c-L\times D_{c}\\
\end{align}
$$

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data = pd.read_csv('/content/Salary.csv')
print(data)
data.isnull().sum()

x = data["YearsExperience"]
y = data["Salary"]

plt.scatter(x,y)
m = 0
c = 0
L = 0.01
n = len(x)
epochs = 10000

for i in range(epochs):
  y_pred = m*x + c
  D_m= (-2/n) * sum(x * (y - y_pred))
  D_c = (-2/n) * sum(y - y_pred)
  m = m - L * D_m
  c = c - L * D_c
print(m,c)
y_pred = m*x+c
print(y_pred)
y_pred1 = m*3+c
print(y_pred1)
plt.scatter(x,y,color='red',label="data point")
plt.plot(x,y_pred,color='blue',label="Linear fit")
plt.xlabel('experience')
plt.ylabel('salary')
plt.title("Linear regression fit line")
plt.legend()
plt.show
#plt.plot([min(x),max(x)],[min(y_pred),max(y_pred)],color='red')
squared_error = (y-y_pred)**2
mse = squared_error.sum()/n
print(mse)
rmse = np.sqrt(mse)
print(rmse)
```
# encoding
```python
from sklearn.preprocessing import LabelEncoder
import numpy as np
data=['Red','Green','Blue','Green','Red']
label_encoder=LabelEncoder()
encoded_data=label_encoder.fit_transform(data)
print(encoded_data)
import pandas as pd
data=pd.DataFrame({'Color':['Red','Green','Blue','Green','Red']})
one_hot_encoded=pd.get_dummies(data,columns=['Color'])
print(one_hot_encoded)
```

# aircraft
```python
import pandas as pd
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score

data = pd.read_csv('aircraft.csv')
print(data)
data.isnull().sum()
X = data[['Flight_distance','Number_of_passenger','Flight_duration','aircraft_type']]
Y = data[['Fuel_consumption',]]
X = pd.get_dummies(X,columns=['Aircraft_type'])
print(X.columns)
X_train,X_test,Y_train,Y_test=train_test_split(X,Y,test_size=0.2,random_state=42)
model=LinearRegression()
model.fit(X_train,Y_train)
Y_pred=model.predict(X_test)
print(Y_pred)
print(len(X_test))
mse = mean_squared_error(Y_test,Y_pred)
print("Mean Squared Error: ", mse)
rmse=np.sqrt(mse)
print("Root Mean Squared Error: ",rmse)
r2 = r2_score(Y_test,Y_pred)
print("R-squared:", r2)
import joblib
joblib.dump(model,'model.pkl')
```

Bias and variance
---

the inability of a ML method to capture true relationship is called bias
the difference in fits between training and testing data sets is called as variance
If a model has low bias and high variance its is called as overfit
If a model has high bias and low variance its is called as underfit

the commonly used methods to find the sweet spot between a simple and complicated model are
regularization
boosting
bagging
