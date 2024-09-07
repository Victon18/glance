# Probability

- Used when there is an aspect of Uncertainty
- Its over a range 0(will not happen) to 1(absolutely happen)
- Use for prediction in ML
- Sample space
---
Set of all possible outcomes of an experiment denotes by $\Omega$

- Event
---
Defined collection of outcomes of an experiment. It is a subset of Sample space ($\Omega$)
Tossing a coin $\Omega = (h,t)$

# Degree of belief

Probability Axiom
---
1. (non-negativity)
---
$P(A) \ge 0$ for an event A

2. Additive
----
In two disjoint events the probability of their union satisfies
$P(A\cup B) = P(A) + P(B)$
$P(A_{1}\cup A_{2}\cup A_{3}\dots)=P(A_{1}+P(A_{2})+P(A_{3})+\dots)$

3.  Normalization
---
The Probability of entire sample is 1 i.e. $P(\Omega)=1$

Law of large numbers
----
The law of large numbers state that the more experiments we run; the closer we get to the expected probability

Gambler's followup
---
It occurs when an individual believes that the certain event is less likely or more likely to happen based on past events

# Random variable
- Given set of possible values from a random experiment.
- A random variable is a set of values that can be any of the values form possible outcomes randomly.

Discrete Random Variable
---
- It's a random variable that can take finite or countable finite value
- Could be category (heads,tails)
- Could be integer (roll of dice)

Continous Random Variable
---
- It's a random variable that can take infinite number of possible values.

Probability Mass function
---
- It gives probability for the discrete random variable
- Its a function i.e. the probability distribution of a discrete random variable and provides values and their possibilities.
- Eg: $\underset{x}{\Sigma}P_{x}(x) = 1$ --> Sum of probability sum up to 1 and $P_{x}\ge0$ --> It's non-negative

Probability Density Function
----
- It gives probability for the continuous random variable.
- Takes out the probability coming within the distinct range of values, as opposed taking only one value.

# Visual representation

- Histogram
----
Used to summarize data by showing the number of points that fall in a specific range.

- Density Plot
----
Plot of smoothed histogram

# Central tendency

Expected Value
----
- Mean of a probability distribution. It represents average value we expect before collecting any data.
- Whereas mean is typically used as when we calculate the mean of sample instead we collect data here

Law of large number
----
It implies that as we increase the number of experiment our mean will converge to expected value.

Measures of central tendency
---
It is a single value that attempts to describe a set of data by identifying the central position within that set

Mean
----
- Commonly used for continuous data
- Tells us the value that is most common
- Is isn't the actual value present in data.
- Sample Mean = $\Large\overline{x}=\frac{\overset{n}{\underset{i}{\Sigma}}xi}{n}$
- Population Mean = $\Large\mu=\frac{\overset{n}{\underset{i}{\Sigma}}xi}{n}$
- In case of data outliers; the mean can get influenced and may give us wrong interpretation of data

Median
---
- Middle value of the dataset after arranging in the order of the magnitude
- Its least affectde by outliers
- median of odd number of dataset = $\Large\frac{n+1}{2}^{th}$ term
- median of even number of dataset = $\Large\frac{\frac{n}{2}^{th}+\frac{n+1}{2}^{th}}{2}$ term

Mode
----
- Most frequent score of the dataset.

# Partition of data
- It is where a sample is divided into equal sized sub-group.
- To divide a probabilty distribution into areas of equal probabilty.

Quartiles
----
- It divides the distribution into four equal parts.
- There are 3 quartiles: Q1(lower),Q2(middle)(median),Q3(upper)

- Formula
-----
- Put the data in order
- Cut the data distribution into 4 equal parts
- The quartiles are the cuts.

Interquartile Range
---
- It is same as range instead its just for quartiles ($Range=Highest-Lowest$)
- the interquartile range is from Q1 to Q3.
- $IQR=Q3-Q1$
- We use IQR to find outliers.
- Its is also resistant to outliers
- it helps in measuring the spread of the dataset
----
- Q1 is the central point between smallest and the median;Q2 is the middle value and Q3 is the highest score
- Q1 tells 25% of the score and are less and 75% of the scores are greater.
- Q2 is the median and 50th pecentile and shows that 50% of the scores are less and 50% are greater.
- Q3 is the 75th percentile and revels that 25% of the scores are greater and 75% of the scores are less

Percentile
---
- Certain
- The 25th percentile is called first quartile.
- The 50th percentile is called median (second quartile).
- The 75th percentile is called third quartile.
- Percenetile range is the difference between third and first quartile.

Decile
---
- It divides the distribution in ten equal parts.

Variance
---
- Variance is the measure of how data points differs from the mean. Its also tells how far data spreads from the average value.
- Measure of spread of data
- denoted by $(\sigma)^{2}$ or square  of standard deviation $\sigma$
-----
Sample variance $\Large (S^{2})=\frac{\overset{n}{\underset{i=1}{\Sigma}}(x_{i}-\overline{x})^{2}}{n-1}$
Population Variance $\LARGE (\sigma^{2})=\frac{\overset{n}{\underset{i=1}{\Sigma}}(x_{i}-\mu)^{2}}{N}$
- n = the total number of observation in sample (sample size)
- N = the total number of observation of population (population size)
- $\LARGE x_{i}$ = values of $\LARGE i^{th}$ observation
- $\LARGE \mu$ = population mean
- $\LARGE \overline{x}$ = sample mean

- Variance of random variable
----
- Concept of expectation takes place.
- Its also called as variance of  probability distribution
- If both R.V. have same mean values; their distribution is completely different.
- $\large E[(x-\mu)^{2}]=\Sigma(x-\mu)^{2}p(x)$
- Computational formula for variance:  $\large var(x)=E[(x-\mu)^{2}]=E(x^{2})-[E(x)]^{2}$

Standard deviation = $\large \sigma=\sqrt{var(x)}$

Covariance
---
- Tells the relationship between two R.V.
- x <------> Y
- if both of the R.V. tend to increase together then it has **positive covariance**
- if both of the R.V. tend to increase together then it has **positive covariance**
- formula
----
Population covariance

$$\LARGE
cov(x,y)=\frac{\Sigma(x_{i}-\overline{x})(y_{j}-\overline{y})}{n}
$$

Sample covariance

$$\LARGE
cov(x,y)=\frac{\Sigma(x_{i}-\overline{x})(y_{j}-\overline{y})}{n-1}
$$

$\large x_{i}$ = the values of x-variable
$\large y_{j}$ = the values of y-variable
$\large \overline{y}$ = the mean of y variable
$\large \overline{x}$ = the mean of x variable
$\large n$= the number of data points

Correlation
----
- measures the strength of relationship.
- correlation coefficient ranges from -1 to 1
- If correlation coefficient is -1 if describes a perfect negative or inverse correlation in which one rises other decreases.
- If correlation coefficient is 1 if describes a perfect positive in which one rises and other as well .
- If the correlation coefficient is 0 then  there is no relationship.
----
correlation coefficient equation
$$\Large
P_{xy} = \frac{cov(x,y)}{\sigma_{x}\cdot\sigma_{y}}
$$
- $\large P_{xy}$ = pearson product moment correlation coefficient.
- $\large cov{x,y}$ = covariance of variable x and y
- $\large \sigma_{x}$ = standard deviation of x
- $\large \sigma_{y}$ = standard deviation of y

Joint probability distribution
----
- probability distribution can represent probability of multiple rvs simultaneously
- probability of both x=x and y=y ie P(x=x,y=y)
eg: probability of drawing 6 and red cards from a deck

$$
\begin{align}
P(6\cap52)&=\frac{2}{52}=\frac{1}{26}\\
P(6)\times P(red)&=\frac{4}{52}\times\frac{26}{52}=\frac{1}{26}
\end{align}
$$

"$\large \cap$" this is referred to as intersection which means it will happen at the same time

Marginal probability
---
- its the probability of single event occurring independent of each other

Sum rule
---
$$\Large
\forall_{x}\in X,P(x=x)=\underset{y}{\Sigma}P(X=x,Y=y)
$$

Conditional probability
----
- The likelihood of an event occurring based on the occurrence of a previous eevent or outcome
- Two events are independent of each other if one event does not affect the probability of another event.
- Two events are dependent of each other if one event does affect the probability of another event.
- If events are independent then it does not relates to the condition probability.
---
$$\Large
P(\frac{A}{B})=\frac{P(A\cap B)}{P(B)};P(B\neq0)
$$

- some special cases
----
- When A and B are disjoint they cannot occur at the same time
$$
\begin{align}
A\cap B&=\phi;\\
P\frac{A}{B}=\frac{P(A\cap B)}{P(B)}&=\frac{P(\phi)}{P(B)}=0
\end{align}
$$

- When B is a subset of A; then whenever B happens A also happens
$$
\begin{align}
P\frac{A}{B}=\frac{P(A\cap B)}{P(B)}&=\frac{P(B)}{P(B)}=1
\end{align}
$$

# Distributions

1. Uniform distribution
----
- Probability is constant over all the possible values of x.
- Median: $\large \frac{a+b}{2}$
- Mean: $\large \frac{c+d}{2}$
- Area of uniform distribution is just a rectangle.

$$
\begin{align}
area&=b\times l \\
&=(b-a)f(x)=1\\
f(x)&=\frac{1}{b-a}
\end{align}
$$

- the probability density function of the uniform distribution

```desmos-graph
top=2; left=-5; right = 5; bottom=-2
---
\operatorname{uniformdist}(2,4)
```

2.Normal distribution
---
- It is symmetrical about the mean showing that data near the mean are more frequent to occur than far from the mean.
- The curve is often reffred as bell curve .
- normal distribution means:
-----
1. mean = median = mode
2. symmetric around the centre
3. 50% values are less than mean and 50% values are more than mean

- All normal distribution have two parts: mean and standard deviation
- Mean is the location parameter and standard deviation is scaling parameter.
- if mean = 0 and standard deviation = 1 then it is called as standard normal deviation
```desmos-graph
top=2; left=-5; right = 5; bottom=-2
---
\operatorname{normaldist}(0,0.5)
```
Empirical rule
---
- It is where most values lie in the normal distribution
- it gives us how much of the data lies within one two and three standard deviation from the mean.
- Around 68% of the values lie within 1 standard deviation from the mean
- Around 95% of the values lie within 2 standard deviation from the mean
- Around 99.7% of the values lie within 1 standard deviation from the mean

$$\LARGE
f(x)=\frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{(x-\mu)^{2}}{2\sigma^{2}}}
$$

Standardizing with z-score
---
The Z-score of an observation is the number of standard deviations it falls above or below the mean.

$$\LARGE
Z-score=\frac{x-\mu}{\sigma}
$$

Geometric distribution
---
used to describe how many trails it takes to success.

p = probability of first trail
1-p = probability of failure
probability of first trail:

$$\LARGE
P(1^{st})= (1-p)^{n-1}p
$$

the mean (expected value ), variance and standard deviation of this wait time:

$$\large
\mu=\frac{1}{p};\sigma^{2}=\frac{1-p}{p^{2}};\sigma=\sqrt{\frac{1-p}{p^{2}}};
$$
here $\mu$'s expected value are sam. On average it takes $\frac{1}{p}$ to get success under the geometric distribution

1. If the P(success) is increased then you dont have to wait for long to success
2. If the P(success) is decresed then you do have to wait for long to success

Bernoulli distribution
---


Binomial distribution
---
- Used to describe number of success in a fixed number of trails.

# hypothesis test

hypothesis
---
- Its is an guess based on knowledge and experience about something
- A claim to test it can be experimental or observational

hypothesis statement
----
- null hypothesis
---
The null hyothesis is always accepted as fact ie its the claim made.

- alternate hypothesis
---
Alternate hypothesis is also called as research hypothesis. It involves claim to be tested.

hypothesis testing
---
its the way to test the result of a survey or expect to see if we have meaningful data

# outliers

