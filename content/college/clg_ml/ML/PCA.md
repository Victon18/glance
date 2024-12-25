 - PCA comes under the Unsupervised Machine Learning category
- The main goal of PCA is to reduce the number of variables in a data collection
- It retaining as much information as feasible.
- It is mainly used for Dimensionality Reduction and important feature selection.
- Correlated features to Independent features
- When should Principal Component Analysis be used in ML?
    - Whenever we need to know our features are independent of each other
    - Whenever we need fewer features from higher features

Variance
---
- For calculating the variation of data distributed across the dimensionality of the graph

Covariance
---
- Calculating dependencies and relationship between features

Standardizing data
---
- Scaling our dataset within a specific range for unbiased output

Covariance matrix
----
- Used for calculating interdependencies between the features or variables
- It helps in reducing it to improve the performance

EigenValues and EigenVectors
---
- The eigenvectors aim to find the largest dataset variance to calculate the Principal Component.
- Eigenvalue means the magnitude of the Eigenvector.
- The eigenvalue indicates variance in a particular direction
- the eigenvector expands or contracts the X-Y (2D) graph without altering the direction.

Dimensionality Reduction
---
- Transpose of original data and multiply it by transposing of the derived feature vector.
- Reducing the features without losing information.


# How Does PCA works?
1. Original Data
2. Normalize the original data (mean =0, variance =1)
3. Calculating covariance matrix
4. Calculating Eigen values, Eigen vectors, and normalized Eigenvectors
5. Calculating Principal Component (PC)
6. Plot the graph for orthogonality between PCs

# Curse of Dimensionality

1. Data Sparsity
----
- Data points become increasingly spread out, making it hard to find patterns or relationships.
----
2. Computational Complexity
----
- The computational burden of algorithms increases exponentially.
----
3. Overfitting
----
- Models become more likely to memorize the training data without generalizing well.
----
4. Distortion of Distance Metrics
----
- Traditional distance metrics become less reliable in measuring proximity.
----
5. Visualization Challenges
----
- Projecting high-dimensional data onto lower dimensions leads to loss of information.
----
6. Data Preprocessing
----
- Identifying relevant features and reducing curse of dimensionality in data science is crucial for effective analysis.
----
7. Algorithmic Efficiency
----
- Algorithms need to be scalable and efficient to handle the complexity of high-dimensional spaces.
----
8. Domain-Specific Challenges
----
- Each domain faces unique challenges in high-dimensional spaces, requiring tailored approaches.
----
9. Interpretability Issues
----
- Understanding the decision-making process of high-dimensional models becomes increasingly difficult.
----
10. Data Storage Requirements
----
- Efficient data storage and retrieval strategies are essential for managing large volumes of high-dimensional data
----


## Advantages of PCA in ML
- Used for Dimensionality Reduction
- PCA will assist you in eliminating all related features, sometimes called multi-collinearity.
- The time required to train your model is substantially shorter because PCA has reduced the number of features.
- PCA aids in overcoming overfitting by eliminating the extraneous features from your dataset
## Disadvantages of PCA in Machine Learning
- Useful for quantitative data but not effective with qualitative data.
- Interpretation of PC is difficult from the original data.

# code
```python
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.decomposition import PCA
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, confusion_matrix, classification_report
import pandas as pd
data = pd.read_csv('/content/WineQT.csv')
data.shape
data.head(10)
data.isnull().sum()
X = data.drop(columns=['quality'])
y = data['quality']
# Split the dataset into training and test sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
# Standardize the features
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
# Logistic Regression without PCA
log_reg = LogisticRegression(max_iter=1000)
log_reg.fit(X_train_scaled, y_train)
y_pred = log_reg.predict(X_test_scaled)
accuracy_without_pca = accuracy_score(y_test, y_pred)
print("Accuracy with PCA:", accuracy_without_pca)
pca = PCA(n_components= 0.96)  # Reduce to 2 principal components
X_train_pca = pca.fit_transform(X_train_scaled)
X_test_pca = pca.transform(X_test_scaled)
X_test_pca.shape
model_with_pca = LogisticRegression(max_iter=200)
model_with_pca.fit(X_train_pca, y_train)
y_pred_with_pca = model_with_pca.predict(X_test_pca)
accuracy_with_pca = accuracy_score(y_test, y_pred_with_pca)
print("Accuracy with PCA:", accuracy_with_pca)
```
