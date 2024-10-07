# Predictive analysis
True predictive analytics involves training a model using one or more samples of data and
then evaluating how well the model performs when applied to a separate sample of data drawn from the same population

predictive analytics can be applied using many different types of models,

## cross-validation
Our goals is to minimize prediction errors (i.e., improve prediction accuracy) when the model is applied to “fresh” or “new” data (e.g., test data).
Fewer prediction errors when applying the model to new data indicate that the model makes more accurate predictions.

It estimates a model based on past data, and then applying that model to new data in order to evaluate the accuracy of the model’s predictions.

we want to avoid overfitting our model to the data on which it is trained,
as this can lead to a model that fits our training data well but that doesn’t generalize to our test data;
applying a trained model to new data can help us evaluate the extent to which we might have overfit a model to the original data.

there are multiple cross-validation frameworks that we can apply when training a model,
and these frameworks can help us improve a model’s predictive performance/accuracy while also reducing the occurrence of overfitting.


- Problem
---
Spliting data into training and testing sets. We should maximize training and testing sets
having maximum amount of training sets will give us best leatrning sets
having maximum amount of training sets will give us best validation results
but everydata point present in training set is  absent in testing set and vice versa

- Solution
---
using cross validation model

### k folds
we do some sort of variation of the two-phase process below
(a) train the model on one set of data,
(b) test the model on a separate set of data.

To perform k-fold cross-validation, we often do the following:

1. Spliting into  taining and testing
---
We split the data into a training data set and a test data set.
Commonly, 80% of the data are randomly selected for the training data set, while the remaining 20% end up in the test data set.

2. Spliting training into sub-samples
----
- We randomly split the training data into two or more (sub)samples,
- which will allow us to train the model in an iterative process.
- The total number of samples we split the data into will be equal to k, where k refers to the number of folds (i.e., resamples).
- we then use the k samples to train (i.e., estimate, build) our model, ny iterating the model-estimation process across k folds of data.
- For each fold, we estimate the model based on pooled data from k-1 samples.

- we then use the kth sample as the validation sample
- **validation** means assess the estimated model’s predictive accuracy on data that weren’t used for that specific model estimation process.
- This process repeats until every sample has served as thei validation sample, for a total of k folds.
- The models’ estimated performance across the k folds is then synthesized.

Specifically, the k cross-validated models
are then tossed out, but the estimated error from those models can be
synthesized (e.g., averaged) to arrive at a performance estimate for the final
model.
With some types of models, the estimated error (e.g., root mean-squared
error, R2) from those models is used to inform the final model estimation.
Note that the final model’s parameter estimates are typically estimated using all of the
available training data.

---

3. The k-fold cross-validation framework can be extended by taking the final trained
model and evaluating its performance based on the test data set that – to this
point – has yet to be used; this is how k-fold cross-validation can be used in a
broader predictive analytics (i.e., predictive modeling) context. It is important to
note, however, that there are other cross-validation approaches we might
choose, such as traditional empirical cross-validation (holdout method) and
leave-one-out cross-validation (LOOCV) – but those are beyond the scope of this
chapter. James, Witten, Hastie, and Tibshirani (2013) provide a nice introduction
to LOOCV; though, in short, LOOCV is a specific instance of k-fold
cross-validation in which k is equal to the number of observations in the training
data. The figure below provides a visual overview of the k-fold cross-validation
process, which we will bring to life in the tutorial portion of this chapter.

# Regularization

- Regularization is a technique that adds a penalty term to the cost function,
- it measures how well the model is performing.
- This penalty term helps control the size of the coefficients (also called weights) in the model.
- Smaller coefficients usually result in a simpler model that is less likely to overfit.
- Regularization helps to balance the trade-off between model complexity and model fit, preventing the model from relying too heavily on any single predictor variable.
