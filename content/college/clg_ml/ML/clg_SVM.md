# Support Vector Machine
- A Support Vector Machine (SVM) is a supervised machine learning algorithm
- It primarily used for classification tasks, but it can also be employed for regression and outlier detection.
- The core idea behind SVM is to find the optimal boundary (or hyperplane)
    - Its seprise that best separates data points of different classes in a high-dimensional space.
- Hard Margin
---
- A hard margin refers to the maximum-margin hyperplane that perfectly separates the data points of different classes without any misclassifications.
---
- Soft Margin
---
- When data contains outliers or is not perfectly separable, SVM uses the soft margin technique.
- This method introduces a slack variable for each data point
    - to allow some misclassifications while balancing between maximizing the margin and minimizing violations.
---

KERNALS
----
- The SVM  algorithm has a technique called the kernel trick.
- The SVM kernel transforms low-dimensional input space to a higher dimensional space,
- it makes non-separable problems separable, useful for non-linear data separation by applying complex data transformations based on labels.
- Linear Kernel
- Polynomial Kernel
- Radial Basis Function (RBF) Kernel / Gaussian Kernel
- Sigmoid Kernel

# Types
1. Linear SVM
----
- When the data is perfectly linearly separable only then we can use Linear SVM.
- Perfectly linearly separable means that the data points can be classified into 2 classes by using a single straight line(if 2D).
----
2. Non-Linear SVM
----
- When the data is not linearly separable then we can use Non-Linear SVM, which
- it means when the data points cannot be separated into 2 classes by using a straight line (if 2D) then
    - we use some advanced techniques like kernel tricks to classify them.
- In most real-world applications we do not find linearly separable data points hence we use kernel tricks to solve them.
----

# advantages
- High-Dimensional Performance
----
- SVM excels in high-dimensional spaces, making it suitable for image classification and gene expression analysis.
----
- Nonlinear Capability
----
- Utilizing kernel functions like RBF and polynomial, SVM effectively handles nonlinear relationships.
----
- Outlier Resilience
----
The soft margin feature allows SVM to ignore outliers, enhancing robustness in spam detection and anomaly detection.
- Binary and Multiclass Support
    SVM is effective for both binary classification and multiclass classification, suitable for applications in text classification.
- Memory Efficiency
    SVM focuses on support vectors, making it memory efficient compared to other algorithms.
# disadvantages
- Slow Training
    - SVM can be slow for large datasets, affecting performance in SVM in data mining tasks.
- Parameter Tuning Difficulty
    - Selecting the right kernel and adjusting parameters like C requires careful tuning, impacting SVM algorithms.
- Noise Sensitivity
    - SVM struggles with noisy datasets and overlapping classes, limiting effectiveness in real-world scenarios.
- Limited Interpretability
    - The complexity of the hyperplane in higher dimensions makes SVM less interpretable than other models.
- Feature Scaling Sensitivity
    - Proper feature scaling is essential; otherwise, SVM models may perform poorly.







SVM (Support Vector Machine)
---
- It can classify both linear and non-linear data
- It does so by creating a hyperplane
- Simplest SVM is LSVM (Linear SVM)

LSVM (Linear SVM)
---
- Data can be classified by an optimal hyperplane
- It draws hyperplane between classes by using margins as the criteria
- Margin is the distance between points near the hyperplane
- Maximum the margin better the accuracy ie maximum margin linear classsifier
- Nearest points around the line are known as support vectors
- Points above the hyperplane is +ve plane and points below the hyperplane is -ve plane

Equation of lines
$$
y = mx+C = 0

$$

Low and High Gamma: Hyper-parameter tuning
---
- This is how we optimise the model
- Low gamma(0) -> only nearest points - when we have enough data points near hyperplane
- High gamma(1) -> nearest as well as some farther points - when we have less data points near hyperplane

Non-Linear SVM
----
- Data cannot be categorized by a line hence we use optimal planes for it
-

$$\LARGE
\begin{align}
y &= W^{aT}x+c\\
\text{Cost Function}\\
\text{Max :- }x_{1}-x_{2} &= \frac{2}{w^{T}}\\
\text{Min :- }x_{1}-x_{2} &= \frac{w^{T}}{2}\\
\end{align}
$$

# Kernals
-

