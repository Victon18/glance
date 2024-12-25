# Evaluation of Classification models

For binary classification models, outcomes are divided into two classes:

- Positive Class:
    This is a phenomenon of interest
    Usually denoted by 1
- Negative Class:
    The phenomenon that does not interest us
    Usually denoted by 0

# Accuracy:

Accuracy is the number of correct predictions divided by the total number of predictions.
It can be calculated as:

$$\large
\frac{\text{number of correct predictions}}{\text{total number of predictions}}
$$

To use accuracy effectively you need to set a baseline.

This baseline accuracy can be found using a dummy classifier.

# Confusion Matrix:

For building a confusion matrix, a table is created where:
- The columns are the ground truth (actually positive and actually negative); and
- The rows are the predicted values (predicted positive and predicted negative).

The configuration of the confusion matrix can be changed, so instead of relying on the position of the quadrants rely on the interaction of rows and columns.

This divides your data into four quadrants:
1. True positive quadrant
---
- This is the top-left quadrant on the confusion matrix.
- It indicates the number of times the model has predicted that the applicant would default, and they did.
---
2. True negative quadrant:
---
- This quadrant is diagonally opposite to the true positive quadrant on the lower-right side of the matrix.
- It indicates the number of times the model has predicted that the applicant would not default, and they did not.
---
3. False-positive quadrant:
---
- This is the top-right quadrant on the confusion matrix.
- It indicates the number of times the algorithm has predicted that the applicant would not default, but they did.
---
4. False-negative quadrant:
---
- This is the lower-left quadrant on the confusion matrix.
- It indicates the number of times the algorithm has predicted that the applicant would default, but they did not
---

You need to notice that the position of these quadrants might change for different formats and usages.

## Accuracy
- Accuracy is the proportion of all classifications that were correct, whether positive or negative.
$$
\begin{align}
\text{Accuracy}&=\frac{\text{correct classification}}{\test{total classification}}\\
&=\frac{TP+TN}{TP+TN+FP+FN}
\end{align}
$$

## Precision

- The proportion of actual positives, out of all the samples that our model has predicted as positive.

$$\large
\begin{align}
Precision&=\frac{\text{corretly classified actual positive}}{\text{everything classifies positive}}\\
&=\frac{TP}{TP+FP}
\end{align}
$$


## Recall (Sensitivity)

- The proportion of correctly predicted positives, out of all the actually positive samples.

$$\large
\begin{align}
Recall &= \frac{\text{correctly classified actual positives}}{\text{all actual positive}}\\
&= \frac{TP}{TP+FN}
\end{align}

$$

## F1 measure

- for both precision and recall to be high you can use a combined metric, i.e., the F1 score.
- The F1 measure is the harmonic mean of precision and recall.

$$\large
\text{F1 score} = \frac{TP}{TP+ \frac{1}{2}(FP+FN)}
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

