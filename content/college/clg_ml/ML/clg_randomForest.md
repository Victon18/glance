- The greater number of trees in the forest leads to higher accuracy and prevents the problem of overfitting.
- It takes less training time as compared to other algorithms.
- It predicts output with high accuracy, even for the large dataset it runs efficiently.
- It can also maintain accuracy when a large proportion of data is missing.
- There should be some actual values in the feature variable of the dataset so that the classifier can predict accurate results rather than a guessed result.
- The predictions from each tree must have very low correlations.

# Random Forest – Working
1. Select random K data points from the training set.
2. Build the decision trees associated with the selected data points(Subsets).
3. Choose the number N for decision trees that you want to build.
4. Repeat Step 1 and 2.
5. For new data points, find the predictions of each decision tree,
    - and assign the new data points to the category that wins the majority votes.

# Advantages & Disadvantages
## Advantages
- Random Forest is capable of performing both Classification and Regression tasks.
- It is capable of handling large datasets with high dimensionality.
- It enhances the accuracy of the model and prevents the overfitting issue.

## Disadvantages
- It is not more suitable for Regression tasks.


# Decision Tree VS Random Forest

|Decision Tree|Random Forest|
|-|-|
|Overfitting|No overfitting|
|Faster to compute|Comparitively slower|
|Formulates rules for prediction|ramdonly select observations|


ensamble learning
---
combining weaker models -> taking all output -> combine them and give prediction

random forest
---
- single decision tree's prediction is easily affected by overfitting
- create multiple decision trees with variation to counter overfitting


bagging
---
1. original trainig data
2. create multiple data sets
3. build multiple classifiers
4. combine classifiers

```python
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import LabelEncoder, StandardScaler
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, classification_report, confusion_matrix

data = pd.read_csv('/content/Iris.csv')
print (data.head(10))
label_encoders = {}
for column in data.select_dtypes(include=['object']).columns:
    le = LabelEncoder()
    data[column] = le.fit_transform(data[column])
    label_encoders[column] = le

data.head(10)
X = data.drop('Species', axis=1)
y = data['Species']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.4, random_state=42)
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
rf_classifier = RandomForestClassifier(n_estimators=1, random_state=42)
rf_classifier.fit(X_train, y_train)
y_pred = rf_classifier.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
print(f"Accuracy: {accuracy}")
print(classification_report(y_test, y_pred))
print(confusion_matrix(y_test, y_pred))
import matplotlib.pyplot as plt
feature_importances = pd.Series(rf_classifier.feature_importances_, index=X.columns)
feature_importances.nlargest(10).plot(kind='barh')
plt.title('Feature Importance')
plt.show()
```
