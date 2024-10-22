Mathematics behind Logistic Regression
---

- y is a discrete variable(0 and 1 in general) in logistic regression.
- the function we use to predict probabilities must satisfy the following criteria:
    1. It is bound between 0 and 1
    2. The function is asymptotic, that is, it can never take a value of 0 or 1.
    3. The function must accommodate the separation in data points that arises in classification.

- the final classes are derived based on whether the probability of a positive class for a data point is greater than the threshold value or not.

sigmoid function
--
A function that satisfies all of these conditions is sigmoid, it can be expressed as:

$$\large
y=\frac{1}{1+e^{-x}}
$$

- As x tends to - ∞, y tends to 0, and as x tends to +∞, y tends to 1. Moreover, for x = 0, y is 0.5.

So overall, the sigmoid function satisfies the above criteria for a classification function.
this equation transforms to:

$$\large
p(b)=\frac{1}{1+e^{-(\beta_{0}+\beta_{1}b)}}
$$

p(b) is the probability of the positive class for an independent variable b.
$\beta_{1}$ is the 'weight' of variable b.

Log Loss Function
---
As you already know, the probability of a positive class can be found using the sigmoid function.

we need to find the values of β that minimize the log loss function.

hence we need to estimate the values of $\beta_{1}$ and $\beta_{0}$
to find optimal beta values we use log loss function

$$\large
L(y|p) = -\frac{1}{n}\sum_{i=1}^{n}[y_{i}\log p_{i}\times(1-y]
$$

- yi is the target variable containing the final class
- pi is the corresponding probability.

We need to calculate different values of the log loss function for different β's to find the minimum value of the log loss function.

Gradient Descent Optimization of the Log Loss
---
We will start with a random value of β, and use a gradient descent approach to iteratively move
toward the minimum loss, and in each iteration, we calculate a new β. The new β is calculated by
using the following formula.

$$\large
\beta_{new}=\beta_{old}-n\frac{\delta L}{\delta\beta}
$$

- As the iterations move further, the log loss decreases and betas move towards optimisation.

- If the gradient value is high, the step that we are gonna take towards the minimum is going to be large, and a smaller one if the gradient value is low.
- We can control the step size through the learning rate η.

- Learning rate for logistic regression is a hyperparameter that can be controlled.

The iteration process will continue until one of the following conditions is satisfied:
1. If the value updates are marginal; that is, they are less than a certain ϵ.
2. If you crossed the threshold on the number of iterations you wanted at the beginning of the method;

For multiple variables, the sigmoid function transforms as follows:

$$\large
p_{i} = \frac{1}{1+e^{-(\beta_{0}+\beta_{i}b_{1i}+\dots)}}
$$

- All the other functions take pi as an input, so they will not change much in terms of notation.

Let us summarize the mathematics behind logistic regression we have learned till now:

1. The sigmoid function can be used to find the function that relates inputs to outputs in case of classification problems.
2. s in the sigmoid are found by minimizing the log loss function

3. There is no open solution to find the minimum of the log loss function, so we try to find
different sets of betas and the corresponding values of the log loss function to find the
minimum. After initializing the process with a random set of betas, we find new betas
using the gradient descent approach.

# Evaluating the model:

Evaluating the model refers to testing model predictability.
How accurate are the model predictions as compared to actual labels.
A model must perform at the same level for both training and testing data sets.
This phenomenon is called generalizability.
Generalizability refers to the ability of a model to make an accurate prediction even in unfamiliar situations.
we must consider two terms associated with model performance—overfitting and underfitting.

Overfitting:
---
Overfitting occurs when a model tries to map every input-output pair in a data set.
Any noise in the data set is not accounted for, which reduces the model's efficiency and accuracy.
When a model is overfitted, it loses generalizability.

Underfitting:
---
Underfitting is the opposite of overfitting.
It occurs when a model cannot identify the underlying trend in the data set.
That prevents the model from learning anything from the data set, thus resulting in less accuracy.
an under-fitted model does not have good generalizability.

it is common to divide your data set into these three parts:

Training data set:
---
A training data set is used to fit the model to the data to estimate the model parameters.
This is the most significant chunk of the data set available.

Validation data set:
---
A validation data set is used to fine-tune the model further and simplify it if it is too complex.

Test data set:
---
After training and validating a model, you can test the model against this data set to evaluate its performance.
The ratio in which you split the data varies case by case.

The process of repeatedly testing and fine-tuning a model using a test data set is called multiple hypothesis testing.
It would be best to avoid this at all costs because it may result in overfitting the model to the data set.
Test set is to be used only when you have a final model to test against unseen data.

what we can do to avoid multiple hypothesis testing:
1. Gather a new test data set, and test the model on it.
2. Split the test data set into smaller parts, and use each part separately.
3. When we have limited data, we can reshuffle the data that forms the training, validation, and test data sets to get a fresh perspective on our data every time we test the model.

While splitting the data, you take random samples from a data set.
This may give rise to variability that was not present initially.
To avoid this, you can use one of the following methods.
1. Collect more unseen data for testing
2. Cross-validate the training data(will be discussed in a later module)


# Evaluation of Classification models

For binary classification models, outcomes are divided into two classes:

- Positive Class:
    This is a phenomenon of interest
    Usually denoted by 1
- Negative Class:
    The phenomenon that does not interest us
    Usually denoted by 0

Accuracy:
---
Accuracy is the number of correct predictions divided by the total number of predictions.
It can be calculated as:

$$\large
\frac{\text{number of correct predictions}}{\text{total number of predictions}}
$$

To use accuracy effectively you need to set a baseline.

This baseline accuracy can be found using a dummy classifier.

Confusion Matrix:
----
For building a confusion matrix, a table is created where:
- The columns are the ground truth (actually positive and actually negative); and
- The rows are the predicted values (predicted positive and predicted negative).

The configuration of the confusion matrix can be changed, so instead of relying on the position of the quadrants rely on the interaction of rows and columns.

This divides your data into four quadrants:
1. True positive quadrant:
    This is the top-left quadrant on the confusion matrix.
    It indicates the number of times the model has predicted that the applicant would default, and they did.
2. True negative quadrant:
    This quadrant is diagonally opposite to the true positive quadrant on the lower-right side of the matrix.
    It indicates the number of times the model has predicted that the applicant would not default, and they did not.
3. False-positive quadrant:
    This is the top-right quadrant on the confusion matrix.
    It indicates the number of times the algorithm has predicted that the applicant would not default, but they did.
4. False-negative quadrant:
    This is the lower-left quadrant on the confusion matrix.
    It indicates the number of times the algorithm has predicted that the applicant would default, but they did not

You need to notice that the position of these quadrants might change for different formats and usages.

- Precision: The proportion of actual positives, out of all the samples that our model has predicted as positive.

$$\large
Precision=\frac{\text{True Positive}}{\text{True Positive - False Positive}}
$$

- Recall (Sensitivity): The proportion of correctly predicted positives, out of all the actually positive3 samples.

$$\large
Recall = \frac{\text{True Positive}}{\text{True Positive + False Negative}}
$$

- F1 measure: If your application demands that both precision and recall be high you can use a combined metric, i.e., the F1 score.
The F1 measure is the harmonic mean of precision and recall.

$$\large
\text{F1 score} = \frac{\text{True Positive}}{\text{True Positive}+ \frac{1}{2}(\text{False Positive + False Negative})}
$$


Probability Predictions:
---
Many classification algorithms do not return explicit labels, i.e., 0s and 1s.
Instead they return probabilities of a data point belonging to one of the cases.
You can set a threshold based on which you can make the final decision.

For instance
- If the probability of belonging to the positive class > threshold, then class = 1.
- If the probability of belonging to the positive class < threshold, then class = 0.
As the threshold increases, recall decreases and precision increases, and vice versa.

Depending on which measure is more important to your model, you can set the threshold accordingly

ROC Curve:
---
A receiver operating characteristic ROC curve signifies the model’s ability to discriminate between classes.
It helps in determining the threshold probability.
It combines the true positive rates and false-positive rates from the confusion matrix and plots them on a graph.

Here are the steps to follow for plotting a ROC curve:
1. Consider various threshold values.
2. For each threshold, calculate TPR and FPR.
3. Plot the data on an FPR (x-axis) vs. TPR (y-axis) grid.

All ROC curves start from the origin and end at the (1,1) point.
Between these two points, the ideal ROC curve is a right-angle line passing through the point (0,1).
The worst model is a straight line passing through (0,0) and (1,1).
All the other real models lie between these two lines.

In most cases, we use discrete threshold values to plot ROC curves, so we get stepwise functions

There are two ways to use the ROC curve to evaluate a model’s performance:
- You can look at the nature of the curve.
    A model that discriminates better will be close to the ideal curve, whereas a poorer model will be closer to the straight line.
- You can calculate the area under the ROC curve, popularly known as the ROC AUC.
    An ideal curve will have a ROC AUC of 1, whereas a random guess will have a ROC AUC of 0.5.

Choosing Evaluation Metrics:
---

Misclassification has more implications in some cases than others.
Based on the problem you are trying to solve, you will have to choose the metric for evaluating the model.
The choice of the modifications you are making to the model will be affected by the evaluation metric.

# Imbalanced Data Sets:
A data set is said to have an imbalance when one class significantly outnumbers the other.
Data imbalance causes certain problems:
- In the case of data with class imbalance, accuracy may not be the right metric
- When a model considers the positive class as a rare event and does not learn the patterns associated with this class.
- As a result, identifying the rare class becomes even more difficult.

To deal with the imbalance in data sets, you need to apply one of the following measures:
- Subsample by reducing samples in the majority class.
- Oversample the minority class.
- Correct the model to compensate for the bias (case-control sampling).

However, you need to be cautious about the artificial balancing of data sets.
You might lose the variance while removing samples in the majority class.
if you upsample the minority class, you might reinforce certain patterns related to the positive class.
This can cause the model to make overconfident predictions.
It is advised to deal with data imbalance in an iterative process where you try different ratios of different classes.


# Python Demonstration

```python
# check for null values
print (bankData.isnull().sum())
# plot
plt.figure()
sb.countplot(x='y',data=bankData)
plt.show()
# created dummy variables for categorical variables
df2 = pd.get_dummies(bankData, columns=['job','marital','default','house','loan','poutcome','education'.'contact'])
# removed the respective original columns such that there was no loss in information.
df2.drop(['job_unkown','marital_unkown','default_unkown','house_unkown','loan_unkown','poutcome_unkown','education_unkown','contact_unkown'], axis=1, inplace=True)
# removed columns which do not effecct the model
df2.drop(['month','month-of-week'], axis=1, inplace=True)
# converting yes and no to 0 and 1.
df2['y'] = df2.map(dict(yes=1, no=0))
# split the data between training and testing data
X = df2.loc[:,['age','duration','pdays','...','...','...']] # features
Y =  df2.loc[:, 'y'] # target
from sklearn.model_selection import train_test_split
X_train,X_test,Y_train,Y_test = train_test_split(X,Y,test_size=0.3,random_state=0)
print(X_train.shape)
print(X_test.shape)
print(Y_train.shape)
print(Y_test.shape)
# imported the LogisticRegression function from the sklearn.linear_model library and created and object
from sklearn.linear_model import LogisticRegression
model = LogisticRegression()
# the coef method to get the β values of all the independent variables.
print (model.coef_)
# make predictions
Y_pred = model.predict(X_test)
from sklearn import metrics
# check the accuracy of the model.
print(metrics.accuracy_score(Y_test,Y_pred))
# plotting confusion matrix
cnf_matrix = metrics.confusion_matrix(Y_test,Y_print)
print(cnf_matrix)
metrics.plot_confusion_matrix(model,X_test,Y_test)
plt.show()
# you evaluated the model using test data where the accuracy score did not improve much.
# You also evaluated the model using roc_auc_score from sklearn.metrics.
```
---
```python
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, confusion_matrix, classification_report

data = pd.read_csv('/content/db.csv')
print(data)
x = data.drop(columns=['loyalty'])
y = data['loyalty']
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.2, random_state=2)
model = LogisticRegression()
model.fit(x_train, y_train)
y_pred = model.predict(x_test)
print(y_pred)
y_pred1 = model.predict(np.array([60,26342,25,27,1.924734272,1]).reshape(1,-1))
print(y_pred1)
accuracy=accuracy_score(y_test,y_pred)
print(accuracy)
conf=confusion_matrix(y_test,y_pred)
print(conf)
class_report=classification_report(y_test,y_pred)
print(class_report)
from sklearn.model_selection import cross_val_score
cv_score = cross_val_score(model, x, y, cv=5)
print(cv_score)
print(np.mean(cv_score))

```
