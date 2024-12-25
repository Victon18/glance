# Decision tree
- Decision Tree is a supervised learning technique for classification and regression, mainly used for classification.
- It is a tree-structured classifier with
    - internal nodes representing features,
    - branches representing decision rules, and
    - leaf nodes representing outcomes.
- Decision nodes make decisions with multiple branches, while leaf nodes represent final outcomes with no branches.
- Decisions are based on the features of the dataset.
- It visually represents possible solutions to a decision problem.
- Called a "decision tree" because it starts from a root node and expands into a tree-like structure.
- Built using the CART (Classification and Regression Tree) algorithm.
- Splits the tree into subtrees based on Yes/No answers to questions.
- A decision tree can contain categorical data (YES/NO) as well as numeric data.

1. Root Node
----
- The highest node, representing the initial feature or decision.
---
2. Internal Nodes (Decision Nodes)
----
- Nodes where decisions are made based on attribute values, leading to further branches.
----
3. Leaf Nodes (Terminal Nodes)
----
- End nodes where predictions or decisions are made, with no further branches.
----
4. Branches (Edges)
----
- Connections between nodes representing decision paths.
----
5. Splitting
----
- Dividing a node into sub-nodes based on a chosen feature and threshold.
----
6. Parent Node
----
- A node that splits into child nodes.
----
7. Child Node
----
- Nodes formed from a parent node's split.
----
8. Decision Criterion
----
- The rule used to split data at a decision node.
----
9. Pruning
----
- Removing branches to prevent overfitting and improve generalization.
----

Information Gain
---
- Information gain is the measurement of changes in entropy after the segmentation of a dataset based on an attribute.
- It calculates how much information a feature provides us about a class.
- According to the value of information gain, we split the node and build the decision tree.
- Algo always tries
    - to maximize the value of information gain, and
    - a node/attribute having the highest information gain is split first.

$$
\text{Information Gain}= \text{Entropy(S)}-\text{[(Weighted Avg)}\times\text{Entropy(each feature)}
$$

Entropy
---
- Entropy is a metric to measure the impurity in a given attribute.
- It specifies randomness in data.

$$
\text{Entropy(s)}=-\text{P(yes)}\log_{2}\text{P(yes)}-\text{P(no)}\log_{2}\text{P(no)}
$$

- S = Total number of samples
- `P(yes)` = probability of yes
- `P(no)` = probability of no

Gini Index
----
- Gini index is a measure of impurity or purity
- It is used while creating a decision tree in the CART(Classification and Regression Tree) algorithm.
- An attribute with the low Gini index should be preferred as compared to the high Gini index.
- It only creates binary splits, and the CART algorithm uses the Gini index to create binary splits.

$$\large
\begin{equation}
\text{Gini Index}=1-\sum^{C}_{i=1}(p_{i})^{2}
\end{equation}
$$

## Advantages of the Decision Tree
- It is simple to understand
- it follows the same process which a human follow while making any decision in real-life.
- It can be very useful for solving decision-related problems.
- It helps to think about all the possible outcomes for a problem.
- There is less requirement of data cleaning compared to other algorithms.

## Disadvantages of the Decision Tree
- The decision tree contains lots of layers, which makes it complex.
- It may have an overfitting issue, which can be resolved using the Random Forest algorithm.


# code
```python
import pandas as pd
df = pd.read_csv('/content/salaries - salaries.csv')
df.head()
inputs = df.drop('salary_more_then_100k',axis='columns')
target = df['salary_more_then_100k']
from sklearn.preprocessing import LabelEncoder
le_company = LabelEncoder()
le_job = LabelEncoder()
le_degree = LabelEncoder()
inputs['company_n'] = le_company.fit_transform(inputs['company'])
inputs['job_n'] = le_job.fit_transform(inputs['job'])
inputs['degree_n'] = le_degree.fit_transform(inputs['degree'])
inputs_n = inputs.drop(['company','job','degree'],axis='columns')
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import accuracy_score
x_train, x_test, y_train, y_test = train_test_split(inputs_n, target, test_size=0.1)
model = DecisionTreeClassifier()
model.fit(x_train,y_train)
predictions = model.predict(x_test)
score = accuracy_score(y_test, predictions)
print("Accuracy:", score)
from sklearn import tree
import matplotlib.pyplot as plt
plt.figure(figsize=(12,8))
tree.plot_tree(model,
                   feature_names=['company_n','job_n','degree_n'],
                   class_names=['0','1'],
                   filled=True)
plt.show()
```
