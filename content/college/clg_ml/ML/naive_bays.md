# Classifier
- probabilistic machine learning model based on Bayes' Theorem
- It is used for classification tasks.
- It assumes that all the features used for prediction are independent.
- Supervised Learning Algorithm

## Baye's Theorem

$$\large
\text{P(A|B)} = \frac{P(B|A)\times P(A)}{P(B)}
$$

## Assumptions of Naïve Bayes
1. Feature independence
----
- The features of the data are conditionally independent of each other, given the class label.
----
2. Continuous features are normally distributed
----
- If a feature is continuous, then it is assumed to be normally distributed within each class.
----
3. Discrete features have multinomial distributions
----
- If a feature is discrete, then it is assumed to have a multinomial distribution within each class.
----
4. Features are equally important
----
- All features are assumed to contribute equally to the prediction of the class label.
----
5. No missing data
----
- The data should not contain any missing values.
----

## Types of Naïve Bayes
1. Gaussian Naïve Bayes
----
- Assumes Features & values are in Gaussian Distribution
- When to Use
    - When your feature variables are continuous and assumed to follow a normal (Gaussian) distribution.
- How It Works
    - It calculates the mean and variance of each feature for each class
    - And uses these parameters to compute the probability of a feature value given a class.
- Example: Predicting whether a flower of a certain species
----
2. Multinomial Naïve Bayes
----
- When to Use
    - Best for discrete count data, often used in text classification where features represent word counts or frequencies.
- How It Works
    - It models the distribution of features as multinomial distributions,
    - making it suitable for features that are counts or frequencies.
- Example: Spam detection in emails by counting the frequency of specific words.
- It is used in discrete counts
----
3. Bernoulli Naïve Bayes
----
- The binomial model is useful if your feature vectors are boolean (i.e. zeros and ones).
- When to Use
    - Suitable for binary/boolean features, where features are present or absent.
- How It Works
    - It assumes that each feature is a binary indicator (0 or 1) and models the
    - its presence or absence of a feature for each class.
- Example: Document classification based on the presence or absence of specific words, regardless of how many times they appear.
----
4. Categorical Naïve Bayes
----
- Useful if the features are categorically distributed
- When to Use
    - When features are categorical (i.e., they take on a limited, fixed number of possible values).
- How It Works
    - It models each feature with a categorical distribution, calculating the probability of each category within each class.
- Example: Predicting user preferences based on categorical data like color choices or brand preferences.
----
# Pro’s&Con’s
## Pro's
- It is easy and fast to predict the class of test data set.
- It also performs well in multi-class prediction
- When the assumption of independence holds, the classifier performs better than other machine learning models,
    - requiring less training data.
- It perform well in case of categorical input variables compared to numerical variable(s).
- For numerical variable, normal distribution is assumed

# Con's
Zero Frequency Problem: Feature present in Test data but not available in Training data
Naïve Bayes is also known as a bad estimator, so the probability outputs from predict_proba should not be taken too seriously.


# code
```python
import numpy as nm
import matplotlib.pyplot as mtp
import pandas as pd

# Importing the dataset
dataset = pd.read_csv('/content/user_behavior_dataset.csv')
dataset.columns
dataset = dataset.drop(columns=['User ID'])
dataset
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
dataset['Device Model'] = le.fit_transform(dataset['Device Model'])
dataset['Operating System'] = le.fit_transform(dataset['Operating System'])
dataset['Gender'] = le.fit_transform(dataset['Gender'])
print(dataset)
x = dataset.drop(['User Behavior Class'],axis =1)
y = dataset['User Behavior Class']
# Splitting the dataset into the Training set and Test set
from sklearn.model_selection import train_test_split
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size = 0.25, random_state = 0)

# Feature Scaling
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
x_train = sc.fit_transform(x_train)
x_test = sc.transform(x_test)
# Fitting Naive Bayes to the Training set
from sklearn.naive_bayes import GaussianNB
classifier = GaussianNB()
classifier.fit(x_train, y_train)

```
