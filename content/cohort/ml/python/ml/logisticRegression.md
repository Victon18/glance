# logistic regression
Logistic regression is a classification learning algorithm that estimates the probability of an instance belonging to a specific class.
Given an input feature X (let's say corresponds to an image), then algorithm produces yhat('Y-Hat'), an estiamted probability of Y.

```python
#-------Libraries---------
import numpy as np
import seaborn as sb
import matplotlib.pyplot as plt
from sklearn.datasets import make_classification
%matplotlib inline

#----------
def generate_data():
    x,y = make_classification(n_samples=5000,
                              n_features=2,
                              n_redundant=0,
                              n_informative=2,
                              random_state=14,
                              n_clusters_per_class=1)
    return x,y
x,y = generate_data()
print(x)
print(y)
```
Estimated Probability
----
- In order to estimate the probabilities of a particular instance using logistic regression algorithm, we use sigmoid function.
- Sigmoid function
---
- A sigmoid function is a mathematical function with a characteristic S-shaped curve.
- It transforms any value in the domain to a number between 0 and 1

Then our regression model estimated probability will be : $Yhat=h(X)=a(X\theta)$ where a = $\LARGE \frac{1}{1+exp(-z)}$

```python
def add_intercept(X):
    """Add an intercept(bias) term to the input features X."""
    intercpt = np.ones((X.shapes[0],1))
    return np.concatenate((intercept,X),axis=1)
def sigmoid(z):
    """Calculate the sigmoid function of the input Z."""
    return 1/(1+np.exp(-z))
def calc_h(X,theta):
    """Calculate the hypothesis (Predicted probabilities) using the sigmoid function."""
    z=np.dot(X,theta)
    h=sigmoid(z)
    return h
# ------------------
def gradient_descent(X,y,theta,alpha,num_iter):
    """Perform gradient desent to optimize the regression parameters"""
    m=y.size
    cost_list=[]
    for i in range(num_iter):
        h=calc_h(X,theta)
        cost=(-y*np.log(h)-(1-y)*np.log(1-h)).mean()
        cost_list.append(cost)

        gradient=np.dot(X.T,(h-y))/m
        theta-=aplha*gradient

        if i % 10000==0:
            print(f'Cost:{cost}')

    return cost_list, theta
# ---------------
def logistic_regression(X,y,alpha=0.01, num_tier=100000):
    """perform logistic regression on the given data and return the optimal parameters."""
    XX=add_intercept(X)
    thata=np.zeros(XX.shape[1])

    cost_list, optimal_parameters=gradient_descent(XX,y,theta,alpha,num_iter)

    return (cost_list, optimal_parameters)
#-------------
X,y=generate_data()
cost_list,optimal_parameters=logistic_regression(X,y)
print(optimal_parameters)
# --------Plotting the cost function---------
plt.plot(range(100000),cost_list)

#----------ploting decision bondary----------
def plot_decision_boundary(x,y,theta):
    plt.figure(figsize=(10,6))

    x1_min, x1_max = X[:,0].min(),X[:,0].max()
    x2_min, x2_max = X[:,1].min(),X[:,1].max()
    xx1 , xx2 = np.meshgrid(np.linspace(x1_min, x1_max), np.linspace(x2_min,x2_max))
    grid=np.c[xx1.ravel(),xx2.ravel()]

    grid=add_intercept(grid)
    probs=calc_h(grid,theta)
    probs=probs.reshape(xx1.shape)

    ax=plt.gca()
    plt.contourf(xx1,xx2,probs,levels=25,cmap=plt.cm.twilight, alpha=0.8)
    plt.contour(xx1,xx2,probs,[0.5],linewidth=2, colors='black')
    plt.scatter(X[:,0],X[:,1],c=y.ravel(),s=40,cmap=plt.cm.twilight, edgecolors='black')

    plt.xlabel("$x_1$")
    plt.ylabel("$x_2$")
    ax.set_xlim([x1_min,x2_max])
    ax.set_ylim([x1_min,x2_max])

    #Customize the plot style
    plt.title("Decision boundary plot",fontsize=18)
    plt.xtics(fontsize=12)
    plt.ytics(fontsize=12)
    plt.colorbar(label="Probability")

    plt.show()

plt.plot_decision_boundary(x,y,optimal_parameters)

```

Sklearn Implimentation
----

```python
from sklearn.linear_model import LogisticRegression
model=LogisticRegression(C=le20,solver='lbfgs')
model.fit(X,y)
preds=model.predict(X)

score_sklearn=(preds==y).mean()
print(f'Score Sklearn: {score_sklearn}')
print(model.intercept_,model.coef_)
```

Assumption testing
----
Assumption testing is a essential step in logistic regression to ensure the validity and reliability of the model's results
These assumption include:

Assumption1- Appopriate outcome type (Must be categorical)
Assumption2- Linearity of independent variable and log odds
Assumption3- No strongly influential outliers
Assumption4- Absence of multicollinearilty
Assumption5- Independence of observations
Assumption6- Suffeciently large sample size

```python
import statsmodels.api as sm
from statsmodels.stats.outliers_influence import OLSInfluence, variance_inflation_factor
from statsmodels.tools import add_constant
%matplotlib inline

def assumption_testing(X,y,theta):
    """Performing assumption testing for logistic regression"""
    xx=add_intercept(X)
    model= sm.Logit(y,XX).fit()
    # Assumption2: Linerity of odd variables and log odd
    print("Assumption2 --> Linerity of odd variables and log odd:")
    print(model.summary())
    print("\n")
    # Assumption3: No Stringly influenced outliers
    print("Assumption3 --> No Stringly influenced outliers:")
    pred_prob= model.predict(XX)
    leverage=np.sum(XX*(1-XX),axis=1)*pred_prob*(1-pred_prob)
    cooks_d=(pred_prob-y)**2/leverage
    print("Cooks distance for each observation:")
    print(cooks_d)
    print("\n")

    # Assumption4: Absence of multicollinearity
    print(" Assumption4 -->  Absence of multicollinearity:")
    vif=[variance_inflation_factor(XX,i)for i in range(XX.shape[1])]
    print("Variance Inflation Factors:")
    print(vif)
    print("\n")

    #Assumption6: Sufficiently large sample size
    print("Assumption6 --> Sufficiently large sample size:" )
    print("Sample size:", len(y))

assumption_testing(x,y,optimal_parameters)

```




