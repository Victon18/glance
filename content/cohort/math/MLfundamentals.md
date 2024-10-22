# cross validation
for making models
1. estimate the parameters for the ML methods (i.e. training the algorithm)
2. evaluating how well the ML method works. (i.e. testing the algorithm)

problem
--
- how to divide data so that all the data is used efficiently.
- among the divided data which chunk to use for trainig and testing to yeild the best results.

K fold cross valdiation
---
- It divided the data into chunks (k).
- It will use one chunk for testing and rest for training the algo.
- keeps track of how well the method did with test data
- Iterates the above steps and try all possible combination and keeps track of performances.
- In the end, every block of data is used for traning and testing.
- We can also compare the methods by seeing how well they performed.

termonoligies
---
1. K-fold :- dividing the data in k chunks.
2. 4-fold :- dividing the data in 4 chunks (25% of data in 4 peices).
3. 10-fold :- dividing the data in 10 chunks (10% of data in 10 peices).
4. Leave one out :- Each individual sample of the data is trained and tested individually, one at a time.

Note
---
- A method that involves a *tuning parameter* (i.e. a parameter the is just sort of guessed)
- we use cross validation to find the best value for that tuning parameter.

# bias and variance

Bias
---
- The inability for a model to capture the true relationship

Variance
---
- The difference in fit between training and testing data set

Overfit
---
- Low variance and high variance leads to overfiting of model

Ideal algo
---
- An ideal algo has low bias and low variability
- An ideal algo can accurately model true relationship and produce consistent predictions across different datasets
- It can be achieving a sweet spot between a simple and complex model
- To achieve sweet spot we use regularization, boosting and bagging


# performance of model

## confusion matrix

- The rows in confusion matrix corresponds to what the machine learning algorithm predicted.
- The columns in confusion matrix corresponds to the known truth.
- the size of the confusion matrix is determined by target we want to predict.
---
- the top left corner contains True Positives -> Positive feature predicted correctly
- the bottom right corner contains True Negatives -> Negative feature predicted correctly
- the bottom left corner contains False Negatives -> Negative features predicted incorrectly.
- the top left corner contains False Positives -> Positive features predicted correctly.
---

<table>
    <tr>
        <td>-</td>
        <td>-</td>
        <td colspan='2' align='center'><b>Actual</b></td>
    </tr>
    <tr>
        <td>-</td>
        <td>-</td>
        <td><i>Loves me</i> </td>
        <td><i>Loves me not</i> </td>
    </tr>
    <tr>
        <td rowspan = '2' align="centre"><b>Predicted</b></td>
        <td><i>Loves me</i></td>
        <td style=' background-color: 0f8c4c;'>True Positive</td>
        <td style=' background-color: C70039;'>False Positive</td>
    </tr>
    <tr>
        <td><i>Loves me not</i></td>
        <td style=' background-color: C70039;'>False Negative</td>
        <td style=' background-color: 0f8c4c;'>True Negative</td>
    </tr>
</table>

---

## Sensitivity
- If correctly identifying positives is the most important thing to do with the data.

$$\large
Sensitivity = frac{\text{True Positive}}{\text{True Positive + False Positive}}
$$
## Specificity
- If correctly identifying negatives is the most important thing to do with the data.

$$\large
Specificity = frac{\text{True Negatives}}{\text{True Negative + False Positive}}
$$


