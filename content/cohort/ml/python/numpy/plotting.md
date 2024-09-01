# matplotlib
## line plot
```python
import numpy as np
import matplotlib.pyplot as plt

x = np.linspace(0,10,100)
y = np.sin(x)

plt.plot(x,y)
plt.xlabel("X-Axis")
plt.ylabel("Y-Axis")
plt.title("Line plot")
plt.show()
```
## scatter plot
```python
x = np.random.rand(100)
y = np.random.rand(100)

plt.scatter(x,y)
plt.xlabel("X-Axis")
plt.ylabel("Y-Axis")
plt.title("Scatter plot")
plt.show()
```
## histogram
```python
data = np.random.normal(100,20,100)

plt.hist(data, bins = 20, color = "purple")
plt.xlabel("Values")
plt.ylabel("Frequency")
plt.title("Histogram")
plt.show()
```
## barplot
```python
x = ['A','B','C','D']
y = [1,5,2,8]

plt.bar(x,y)
plt.xlabel("Categories")
plt.ylabel("Values")
plt.title("Bar plot")
plt.show()
```
## pie chart
```python
labels = ['A','B','C','D']
values = [10,20,30,40]

plt.pie(values, labels = labels, startangle = 90, autopct = "%1.1f%%")
plt.axis("equal")
plt.title("Pie chart")
plt.show()
```
## box plot
```python
data = [np.random.normal(50,10,100), np.random.normal(80,20,100), np.random.normal(40,12,100)]

plt.boxplot(data)
plt.xlabel("Categories")
plt.ylabel("Values")
plt.title("Box Plot")
plt.show()
```
# seaborn
## line plot
```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sb

x = np.linspace(0,10,100)
y = np.sin(x)
sb.lineplot(x,y)
plt.show()
```
## pair plot
```python
data = np.random.multivariate_normal([0,0],[[1,0.5],[0.5,1]],100)
sb.pairplot(data)
plt.show()
```
## heatmap
```python
data = np.random.random(0,10)
sb.heatmap(data)
plt.show()
```
## voilin plot
```python
data = np.random.normal(0,1,100)
sb.lineplot(data)
plt.show()
```

