# gradient_descent
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

```
