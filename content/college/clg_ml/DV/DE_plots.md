# matplotlib
- Types of Data
1. Numerical Data
2. Categorical Data
```python
# import the library
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
plt.style.use('default')
```
## 2D Line plot
- Bivariate Analysis
- categorical -> numerical and numerical -> numerical
- Use case - Time series data, Comparing data sets, Communicating numbers
- are used to visualize data by connecting points with lines
- plot -> x-axis,y-axis
```python
# plotting a simple function
price = [48000,54000,57000,49000,47000,45000]
year = [2015,2016,2017,2018,2019,2020]
plt.plot(year,price)
# from a pandas dataframe
batsman = pd.read_csv('/content/sharma-kohli.csv')
batsman
plt.plot(batsman['index'],batsman['V Kohli'])
```
---
```python
# plotting multiple plots
plt.plot(batsman['index'],batsman['V Kohli'])
plt.plot(batsman['index'],batsman['RG Sharma'])
```
---
- xlabel -> naming x-axis
- ylabel -> naming y-axis
- title -> name of graph
```python
# labels title
plt.plot(batsman['index'],batsman['V Kohli'])
plt.plot(batsman['index'],batsman['RG Sharma'])
plt.title('Rohit Sharma Vs Virat Kohli Career Comparison')
plt.xlabel('Season')
plt.ylabel('Runs Scored')
```
---
- color -> color of the line
- linestyle -> type of line drawn
    - Solid ‘-‘, Dashed ‘--’, Dotted ':', Dashdot '-.', None ' '
- linewidth -> width of line
- marker -> shapes for the point of actual plotting
- markersize -> size of marker

| symbol        | Name           |
| ------------- | -------------- |
| 'o'           | Circle         |
| '*'           | Star           |
| '.'           | Point          |
| ','           | Pixel          |
| 'x'           | X              |
| 'X'           | X (filled)     |
| '+'           | Plus           |
| 'P'           | Plus (filled)  |
| 's'           | Square         |
| 'D'           | Diamond        |
| 'd'           | Diamond (thin) |
| 'p'           | Pentagon       |
| 'H'           | Hexagon        |
| 'h'           | Hexagon        |
| 'v'           | Triangle Down  |
| '^'           | Triangle Up    |
| '<'           | Triangle Left  |
| '>'           | Triangle Right |
| '1'           | Tri Down       |
| '2'           | Tri Up         |
| '3'           | Tri Left       |
| '4'           | Tri Right      |
| 'staightline' | Vline          |
| '_'           | Hline          |


```python
# colors(hex) and line(width and style) and marker(size)
plt.plot(batsman['index'],batsman['V Kohli'],color='#D9F10F')
plt.plot(batsman['index'],batsman['RG Sharma'],color='#FC00D6')
plt.title('Rohit Sharma Vs Virat Kohli Career Comparison')
plt.xlabel('Season')
plt.ylabel('Runs Scored')
plt.plot(batsman['index'],batsman['VKohli'],color='#D9F10F',linestyle='solid',linewidth=3)
plt.plot(batsman['index'],batsman['RGSharma'],color='#FC00D6',linestyle='dashdot',linewidth=2)
plt.title('Rohit Sharma Vs Virat Kohli Career Comparison')
plt.xlabel('Season')
plt.ylabel('Runs Scored')
plt.plot(batsman['index'],batsman['VKohli'],color='#D9F10F',linestyle='solid',linewidth=3,marker='D',markersize=10)

plt.plot(batsman['index'],batsman['RGSharma'],color='#FC00D6',linestyle='dashdot',linewidth=2,marker='o')
plt.title('Rohit Sharma Vs Virat Kohli Career Comparison')
plt.xlabel('Season')
plt.ylabel('Runs Scored')
```
---
- legend attribute
    1. shadow: [None or bool] Whether to draw a shadow behind the legend.It’s Default value is None.
    2. markerscale: [None or int or float] The relative size of legend markers compared with the originally drawn ones.
    3. numpoints: [None or int] The number of marker points in the legend when creating a legend entry for a Line2D (line).
    4. fontsize: The font size of the legend.If the value is numeric the size will be the absolute font size in points.
    5. facecolor: [None or “inherit” or color] The legend’s background color.
    6. edgecolor: [None or “inherit” or color] The legend’s background patch edge color.

```python
# legend -> location
plt.plot(batsman['index'],batsman['VKohli'],color='#D9F10F',linestyle='solid',linewidth=3,marker='D',marke
rsize=10,label='Virat')
plt.plot(batsman['index'],batsman['RGSharma'],color='#FC00D6',linestyle='dashdot',linewidth=2,marker='o',la
bel='Rohit')
plt.title('Rohit Sharma Vs Virat Kohli Career Comparison')
plt.xlabel('Season')
plt.ylabel('Runs Scored')
plt.legend(loc='upper right')
#for outside
plt.legend(bbox_to_anchor=(0.75, 1.15), ncol=2)
```
---
- xlim -> limit for x-axis of a specified range
- ylim -> limit for y-axis of a specified range
```python
# limiting axes
price = [48000,54000,57000,49000,47000,45000,4500000]
year = [2015,2016,2017,2018,2019,2020,2021]
plt.plot(year,price)
plt.ylim(0,75000)
plt.xlim(2017,2019)
```
---
- grid -> enables grid
- show -> to draw plots
```python
# grid
plt.plot(batsman['index'],batsman['V Kohli'],color='#D9F10F',linestyle='solid',linewidth=3,marker='D',markersize=10)
plt.plot(batsman['index'],batsman['RG Sharma'],color='#FC00D6',linestyle='dashdot',linewidth=2,marker='o')
plt.title('Rohit Sharma Vs Virat Kohli Career Comparison')
plt.xlabel('Season')
plt.ylabel('Runs Scored')
plt.grid()
# show
plt.plot(batsman['index'],batsman['V Kohli'],color='#D9F10F',linestyle='solid',linewidth=3,marker='D',markersize=10)
plt.plot(batsman['index'],batsman['RG Sharma'],color='#FC00D6',linestyle='dashdot',linewidth=2,marker='o')
plt.title('Rohit Sharma Vs Virat Kohli Career Comparison')
plt.xlabel('Season')
plt.ylabel('Runs Scored')
plt.grid()
plt.show()
```
## Scatter Plots
- Bivariate Analysis
- numerical vs numerical
- uses dots to represent values for two different numeric variables.
- The position of each dot on the horizontal and vertical axis indicates values for an individual data point
- Use case - Finding correlation

```python
# plt.scatter simple function
x = np.linspace(-10,10,50)
y = 10*x + 3 + np.random.randint(0,300,50)
y
plt.scatter(x,y)
# plt.scatter on pandas data
df = pd.read_csv('/content/batter.csv')
df = df.head(50)
df
plt.scatter(df['avg'],df['strike_rate'],color='red',marker='+')
plt.title('Avg and SR analysis of Top 50 Batsman')
plt.xlabel('Average')
plt.ylabel('SR')
```
---
- s is the size parameter for the points in the scatter plot.
- Multiplying size by 10 scales the size of the points so they are large enough to be visible.

```python
# marker
# size
tips = sns.load_dataset('tips')
# slower
plt.scatter(tips['total_bill'],tips['tip'],s=tips['size']*20)
# scatterplot using plt.plot
# faster
plt.plot(tips['total_bill'],tips['tip'],'o')
# 'o' makes scatter plot in the end
# plt.plot vs plt.scatter
```
## Bar chart
- Bivariate Analysis
- plots numeric values for levels of a categorical feature as bars.
- Levels are plotted on one chart axis, and values are plotted on the other axis.
- Each categorical value claims one bar, and the length of each bar corresponds to the bar's value.
- Use case - Aggregate analysis of groups

- The function plt.xticks() is used to set:
    - x-tick positions (where the ticks are placed on the axis).
    - x-tick labels (what is displayed at each tick position).

```python
# simple bar chart
children = [10,20,40,10,30]
colors = ['red','blue','green','yellow','pink']
plt.bar(colors,children,color='black')
# bar chart using data
# horizontal bar chart
plt.barh(colors,children,color='black')
# color and label
df = pd.read_csv('/content/batsman_season_record.csv')
df.shape
plt.bar(np.arange(df.shape[0]) - 0.2,df['2015'],width=0.2,color='yellow')
plt.bar(np.arange(df.shape[0]),df['2016'],width=0.2,color='red')
plt.bar(np.arange(df.shape[0]) + 0.2,df['2017'],width=0.2,color='blue')
plt.xticks(np.arange(df.shape[0]), df['batsman'])
plt.show()
```
---
```python
np.arange(df.shape[0])
children = [10,20,40,10,30]
colors = ['red red red red red red','blue blue blue blue','green green green green green','yellow yellow yellow yellow ','pink pinkpinkpink']
plt.bar(colors,children,color='black')
plt.xticks(rotation='vertical')
# Stacked Bar chart
plt.bar(df['batsman'],df['2017'],label='2017')
plt.bar(df['batsman'],df['2016'],bottom=df['2017'],label='2016')
plt.bar(df['batsman'],df['2015'],bottom=(df['2016'] + df['2017']),label='2015')
plt.legend()
plt.show()
```
## Histogram
- Univariate Analysis
- It is a chart that plots the distribution of a numeric variable's values as a series of bars.
- Each bar typically covers a range of numeric values called a bin or class;
- a bar's height indicates the frequency of data points with a value within the corresponding bin.
- Use case - Frequency Count

```python
# simple data
data = [32,45,56,10,15,27,61]
plt.hist(data,bins=[10,25,40,55,70])
# on some dataset
df = pd.read_csv('/content/vk.csv')
df
plt.hist(df['batsman_runs'],bins=[0,10,20,30,40,50,60,70,80,90,100,110,120])
plt.show()
# logarithmic scale (log)
# is used Handling Large Range of Frequencies, Better Visualization of Skewed Data, Improving Clarity for Large Datasets
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
arr = np.load('/content/big-array.npy')
plt.hist(arr,bins=[10,20,30,40,50,60,70],log=True)
#,log=True
plt.show()
```
## Pie Chart
- Univariate/Bivariate Analysis
- It representing data in a circular form, with each slice of the circle representing a fration  of the whole
- Categorical vs numerical
- Use case - To find contribution on a standard scale

```python
# simple data
data = [23,45,100,20,49]
subjects = ['eng','science','maths','sst','hindi']
plt.pie(data,labels=subjects,autopct='%0.1f%%',explode=[0.3,0,0,0,0])
plt.show()
# dataset
df = pd.read_csv('/content/gayle-175.csv')
df
plt.pie(df['batsman_runs'],labels=df['batsman'],autopct='%0.1f%%')
plt.show()
# percentage and colors
plt.pie(df['batsman_runs'],labels=df['batsman'],autopct='%0.1f%
%',colors=['blue','green','yellow','pink','cyan','brown'])
plt.show()
# explode shadow
plt.pie(df['batsman_runs'],labels=df['batsman'],autopct='%0.1f%
%',explode=[0.3,0,0,0,0,0.1],shadow=True)
plt.show()
```
## Changing styles
```python
plt.style.available
plt.style.use('dark_background')
arr = np.load('/content/big-array.npy')
plt.hist(arr,bins=[10,20,30,40,50,60,70],log=True)
plt.show()
```
## Save figure
```python
arr = np.load('/content/big-array.npy')
plt.hist(arr,bins=[10,20,30,40,50,60,70],log=True)
plt.savefig('sample.png')
```

## Colored Scatterplots
```python
iris = pd.read_csv('iris.csv')
iris.sample(5)
iris['Species'] = iris['Species'].replace({'Iris-setosa':0,'Iris-versicolor':1,'Iris-virginica':2})
iris.sample(5)
plt.scatter(iris['SepalLengthCm'],iris['PetalLengthCm'],c=iris['Species'],cmap='jet',alpha=0.7)
plt.xlabel('Sepal Length')
plt.ylabel('Petal Length')
plt.colorbar()
# cmap and alpha
```

## Plot size
```python
plt.figure(figsize=(15,7))
plt.scatter(iris['SepalLengthCm'],iris['PetalLengthCm'],c=iris['Species'],cmap='jet',alpha=0.7)
plt.xlabel('Sepal Length')
plt.ylabel('Petal Length')
plt.colorbar()
```

## Annotations
```python
batters = pd.read_csv('batter.csv')
batters.shape
sample_df = df.head(100).sample(25,random_state=5)
print(sample_df)
plt.figure(figsize=(18,10))
plt.scatter(sample_df['avg'],sample_df['strike_rate'],s=sample_df['runs'])
for i in range(sample_df.shape[0]):
plt.text(sample_df['avg'].values[i],sample_df['strike_rate'].values[i],sample_df['batter'].values[i])
x = [1,2,3,4]
y = [5,6,7,8]
plt.scatter(x,y)
plt.text(1,5,'Point 1')
plt.text(2,6,'Point 2')
plt.text(3,7,'Point 3')
plt.text(4,8,'Point 4',fontdict={'size':12,'color':'brown'})
```
## Horizontal and Vertical lines
```python
plt.figure(figsize=(18,10))
plt.scatter(sample_df['avg'],sample_df['strike_rate'],s=sample_df['run
s'])
plt.axhline(130,color='red')
plt.axhline(140,color='green')
plt.axvline(30,color='red')
for i in range(sample_df.shape[0]):
plt.text(sample_df['avg'].values[i],sample_df['strike_rate'].values[i], sample_df['batter'].values[i])
```
## Subplots
```python
# A diff way to plot graphs
batters.head()
plt.figure(figsize=(15,6))
plt.scatter(batters['avg'],batters['strike_rate'])
plt.title('Something')
plt.xlabel('Avg')
plt.ylabel('Strike Rate')
plt.show()
fig,ax = plt.subplots(figsize=(15,6))
ax.scatter(batters['avg'],batters['strike_rate'],color='red',marker='+')
ax.set_title('Something')
ax.set_xlabel('Avg')
ax.set_ylabel('Strike Rate')
fig.show()
# batter dataset
fig, ax = plt.subplots(nrows=2,ncols=1,sharex=True,figsize=(10,6))
ax[0].scatter(batters['avg'],batters['strike_rate'],color='red')
ax[1].scatter(batters['avg'],batters['runs'])
ax[0].set_title('Avg Vs Strike Rate')
ax[0].set_ylabel('Strike Rate')
ax[1].set_title('Avg Vs Runs')
ax[1].set_ylabel('Runs')
ax[1].set_xlabel('Avg')
Text(0.5, 0, 'Avg')
fig, ax = plt.subplots(nrows=2,ncols=2,figsize=(10,10))
ax[0,0].
ax[0,1].scatter(batters['avg'],batters['runs'])
ax[1,0].hist(batters['avg'])
ax[1,1].hist(batters['runs'])
fig = plt.figure()
ax1 = fig.add_subplot(2,2,1)
ax1.scatter(batters['avg'],batters['strike_rate'],color='red')
ax2 = fig.add_subplot(2,2,2)
ax2.hist(batters['runs'])
ax3 = fig.add_subplot(2,2,3)
ax3.hist(batters['avg'])
fig, ax = plt.subplots(nrows=2,ncols=2,sharex=True,figsize=(10,10))
ax[1,1]
```
## 3D Scatter Plots
```python
batters
fig = plt.figure()
ax = plt.subplot(projection='3d')
ax.scatter3D(batters['runs'],batters['avg'],batters['strike_rate'],marker='+')
ax.set_title('IPL batsman analysis')
ax.set_xlabel('Runs')
ax.set_ylabel('Avg')
ax.set_zlabel('SR')
```
## 3D Line Plot
```python
x = [0,1,5,25]
y = [0,10,13,0]
z = [0,13,20,9]
fig = plt.figure()
ax = plt.subplot(projection='3d')
ax.scatter3D(x,y,z,s=[100,100,100,100])
ax.plot3D(x,y,z,color='red')
```
# 3D Surface Plots
```python
x = np.linspace(-10,10,100)
y = np.linspace(-10,10,100)
xx, yy = np.meshgrid(x,y)
z = xx**2 + yy**2
z.shape
fig = plt.figure(figsize=(12,8))
ax = plt.subplot(projection='3d')
p = ax.plot_surface(xx,yy,z,cmap='viridis')
fig.colorbar(p)
z = np.sin(xx) + np.cos(yy)
fig = plt.figure(figsize=(12,8))
ax = plt.subplot(projection='3d')
p = ax.plot_surface(xx,yy,z,cmap='viridis')
fig.colorbar(p)
z = np.sin(xx) + np.log(xx)
fig = plt.figure(figsize=(12,8))
ax = plt.subplot(projection='3d')
p = ax.plot_surface(xx,yy,z,cmap='viridis')
fig.colorbar(p)
z = np.sin(xx) + np.log(xx)
p = ax.plot_surface(xx,yy,z,cmap='viridis')
fig = plt.figure(figsize=(12,8))
ax = plt.subplot(projection='3d')
p = ax.plot_surface(xx,yy,z,cmap='viridis')
fig.colorbar(p)
```
## Contour Plots
```python
fig = plt.figure(figsize=(12,8))
ax = plt.subplot()
p = ax.contour(xx,yy,z,cmap='viridis')
fig.colorbar(p)
fig = plt.figure(figsize=(12,8))
ax = plt.subplot()
p = ax.contourf(xx,yy,z,cmap='viridis')
fig.colorbar(p)
z = np.sin(xx) + np.cos(yy)
fig = plt.figure(figsize=(12,8))
ax = plt.subplot()
p = ax.contourf(xx,yy,z,cmap='viridis')
fig.colorbar(p)
```
## Heatmap
```python
delivery = pd.read_csv('/content/IPL_Ball_by_Ball_2008_2022.csv')
delivery.head()
temp_df = delivery[(delivery['ballnumber'].isin([1,2,3,4,5,6])) & (delivery['batsman_run']==6)]
grid = temp_df.pivot_table(index='overs',columns='ballnumber',values='batsman _run',aggfunc='count')
plt.figure(figsize=(20,10))
plt.imshow(grid)
plt.yticks(delivery['overs'].unique(), list(range(1,21)))
plt.xticks(np.arange(0,6), list(range(1,7)))
plt.colorbar()
```
## Pandas Plot()
```python
# on a series
s = pd.Series([1,2,3,4,5,6,7])
s.plot(kind='pie')
# can be used on a dataframe as well
import seaborn as sns
tips = sns.load_dataset('tips')
tips['size'] = tips['size'] * 100
tips.head()
# Scatter plot -> labels -> markers -> figsize -> color -> cmap
tips.plot(kind='scatter',x='total_bill',y='tip',title='Cost
Analysis',marker='+',figsize=(10,6),s='size',c='sex',cmap='viridis')
# 2d plot
# dataset = 'https://raw.githubusercontent.com/m-mehdi/pandas_tutorials/main/weekly_stocks.csv'
stocks = pd.read_csv('https://raw.githubusercontent.com/m-mehdi/pandas_tutorials/main/weekly_stocks.csv')
stocks.head()
# line plot
stocks['MSFT'].plot(kind='line')
stocks.plot(kind='line',x='Date')
stocks[['Date','AAPL','FB']].plot(kind='line',x='Date')
# bar chart -> single -> horizontal -> multiple
# using tips
temp = pd.read_csv('/content/batsman_season_record.csv')
temp.head()
tips.groupby('sex')['total_bill'].mean().plot(kind='bar')
temp['2015'].plot(kind='bar')
temp.plot(kind='bar')
# stacked bar chart
temp.plot(kind='bar',stacked=True)
# histogram
# using stocks
stocks[['MSFT','FB']].plot(kind='hist',bins=40)
# pie -> single and multiple
df = pd.DataFrame(
{
'batsman':['Dhawan','Rohit','Kohli','SKY','Pandya','Pant'],
'match1':[120,90,35,45,12,10],
'match2':[0,1,123,130,34,45],
'match3':[50,24,145,45,10,90]
}
)
df.head()
df['match1'].plot(kind='pie',labels=df['batsman'].values,autopct='%0.1f%%')
# multiple pie charts
df[['match1','match2','match3']].plot(kind='pie',subplots=True,figsize=(15,8))
# multiple separate graphs together
# using stocks
stocks.plot(kind='line',subplots=True)
# on multiindex dataframes
# using tips
tips.pivot_table(index=['day','time'],columns=['sex','smoker'],values='total_bill',aggfunc='mean').plot(kind='pie',subplots=True,figsize=(20,10))
array([<matplotlib.axes._subplots.AxesSubplot object at
tips
stocks.plot(kind='scatter3D')
```
# Seaborn
Why Seaborn?
---
- provides a layer of abstraction hence simpler to use
1. better aesthetics
2. more graphs included

--
Seaborn Roadmap
---
- Types of Functions
1. Figure Level
2. Axis Level
- Main Classification
1. Relational Plot
2. Distribution Plot
3. Categorical Plot
4. Regression Plot
5. Matrix Plot
6. Multiplots
# Relational Plot
- to see the statistical relation between 2 or more variables.
- Bivariate Analysis
-Plots under this section
1. scatterplot
2. lineplot
```python
import seaborn as sns
import matplotlib.pyplot as plt
import plotly.express as px
tips = sns.load_dataset('tips')
tips
# scatter plot -> axes level function
sns.scatterplot(data=tips, x='total_bill',y='tip',hue='sex',style='time',size='size')
# relplot -> figure level -> square shape
sns.relplot(data=tips, x='total_bill', y='tip', kind='scatter',hue='sex',style='time',size='size')
# scatter using relplot -> size and hue
# style semantics
# line plot
gap = px.data.gapminder()
temp_df = gap[gap['country'] == 'India']
temp_df
# axes level function
sns.lineplot(data=temp_df, x='year', y='lifeExp')
# using relpplot
sns.relplot(data=temp_df, x='year', y='lifeExp', kind='line')
# hue -> style
temp_df = gap[gap['country'].isin(['India','Brazil','Germany'])]
temp_df
sns.relplot(kind='line', data=temp_df, x='year', y='lifeExp',
hue='country', style='continent', size='continent')
sns.lineplot(data=temp_df, x='year', y='lifeExp', hue='country')
# facet plot -> figure level function -> work with relplot
# it will not work with scatterplot and lineplot
sns.relplot(data=tips, x='total_bill', y='tip', kind='line',col='sex', row='day')
# col wrap
sns.relplot(data=gap, x='lifeExp', y='gdpPercap', kind='scatter',col='year', col_wrap=3)
sns.scatterplot(data=tips, x='total_bill', y='tip', col='sex',row='day')
```
# Distribution Plots
- used for univariate analysis
- used to find out the distribution
- Range of the observation
- Central Tendency
- is the data bimodal?
- Are there outliers?
- Plots under distribution plot
1. histplot
2. kdeplot
---
- It depicts the probability density at different values in a continuous variable.
- It visually represents the distribution of data, providing insights into its shape, central tendency, and spread.
- It is particularly useful when dealing with continuous data
- when you want to explore the distribution without making assumptions about a specific parametric form
- assuming the data follows a normal distribution.
- smooths the observations with a Gaussian kernel, producing a continuous density estimate
---
3. rugplot
---
- displays individual data points along a single axis, usually the x-axis, as small lines or ticks.
---
```python
# figure level -> displot
# axes level -> histplot -> kdeplot -> rugplot
# plotting univariate histogram
sns.histplot(data=tips, x='total_bill')
sns.displot(data=tips, x='total_bill', kind='hist')
# bins parameter
sns.displot(data=tips, x='total_bill', kind='hist',bins=2)
# It’s also possible to visualize the distribution of a categorical variable using the logic of a histogram.
# Discrete bins are automatically set for categorical variables
# countplot
sns.displot(data=tips, x='day', kind='hist')
# hue parameter
sns.displot(data=tips, x='tip', kind='hist',hue='sex')
# element -> step
sns.displot(data=tips, x='tip', kind='hist',hue='sex',element='step')
titanic = sns.load_dataset('titanic')
titanic
sns.displot(data=titanic, x='age',kind='hist',element='step',hue='sex')
# faceting using col and row -> not work on histplot function
sns.displot(data=tips, x='tip', kind='hist',col='sex',element='step')
# kdeplot
# Rather than using discrete bins, a KDE plot smooths the observations with a Gaussian kernel, producing a continuous density estimate
sns.kdeplot(data=tips,x='total_bill')
sns.displot(data=tips,x='total_bill',kind='kde')
# hue -> fill
sns.displot(data=tips,x='total_bill',kind='kde',hue='sex',fill=True,height=10,aspect=2)
# Rugplot
# Plot marginal distributions by drawing ticks along the x and y axes.
# This function is intended to complement other plots by showing the location of individual observations in an unobtrusive way.
sns.kdeplot(data=tips,x='total_bill')
sns.rugplot(data=tips,x='total_bill')
# Bivariate histogram
# A bivariate histogram bins the data within rectangles that tile the plot
# and then shows the count of observations within each rectangle with the fill color
# sns.histplot(data=tips, x='total_bill', y='tip')
sns.displot(data=tips, x='total_bill', y='tip',kind='hist')
# Bivariate Kdeplot
# a bivariate KDE plot smoothes the (x, y) observations with a 2D Gaussian
sns.kdeplot(data=tips, x='total_bill', y='tip')
```
# Matrix Plot
- No figure level maps
- Heatmap
- Clustermap
```python
# Heatmap
# Plot rectangular data as a color-encoded matrix
temp_df = gap.pivot(index='country',columns='year',values='lifeExp')
# axes level function
plt.figure(figsize=(15,15))
sns.heatmap(temp_df)
# annot
temp_df = gap[gap['continent'] =='Europe'].pivot(index='country',columns='year',values='lifeExp')
plt.figure(figsize=(15,15))
sns.heatmap(temp_df,annot=True,linewidth=0.5, cmap='summer')
# linewidth
# cmap
# Clustermap
# Plot a matrix dataset as a hierarchically-clustered heatmap.
# This function requires scipy to be available.
iris = px.data.iris()
iris
sns.clustermap(iris.iloc[:,[0,1,2,3]])
```
# Categorical Plot
1. Categorical Scatter Plot
---
- Stripplot
---
- displays individual data points for one or more categorical variables, often overlaid on a box or violin plot.
- It shows the distribution and concentration of data points, highlighting any potential outliers.
---
- Swarmplot
---
- It displays individual data points for one or more categorical variables, similar to a strip plot,
- it adjusts points to avoid overlap.
- It provides a clear view of the distribution and density of the data.
---
2. Categorical Distribution Plots
----
- Boxplot
---
- It displays the distribution of a dataset through its
    - quartiles,
    - highlighting the median,
    - interquartile range, and
    - potential outliers.
- It provides a visual summary of the data's central tendency, dispersion, and skewness.
---
- Violinplot
----
- It combines a box plot with a kernel density plot, showing
    - the distribution,
    - probability density,
    - central tendencies of the data.
- It provides a detailed view of the data's distribution, highlighting variations and multimodalities.
----
3. Categorical Estimation Plot -> for central tendency
---
- Barplot
---
- It displays categorical data with rectangular bars,
- the length of each bar represents the value of the corresponding category.
- It is useful for comparing quantities across different categories.
---
- Pointplot
---
- This method is used to show point estimates and confidence intervals using scatter plot glyphs.
- It represents an estimate of central tendency for a numeric variable
- by the position of scatter plot points and provides some indication of the uncertainty around that estimate using error bars.
---
- Countplot
---
- A count plot (countplot) is a bar plot that shows the frequency of occurrences for each category in a categorical variable.
- It visualizes the count of each unique value in the data.
---

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.catplot(data=tips,x='sex',kind='count')
sns.catplot(data=tips,x='sex',y='total_bill',kind='bar')
sns.catplot(data=tips,x='sex',y='total_bill',kind='point')
sns.catplot(data=tips,x='sex',y='total_bill',kind='violin')
sns.catplot(data=tips,x='sex',y='total_bill',kind='box')
sns.catplot(data=tips,x='sex',y='total_bill',kind='strip')
sns.catplot(data=tips,x='sex',y='total_bill',kind='swarm')
plt.show()
```
