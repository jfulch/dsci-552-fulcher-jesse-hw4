# DSCI 552 - Homework 4

- **Name:** Jesse Fulcher
- **GitHub Username:** `jfulch`
- **Notebook:** [Fulcher_Jesse_HW4.ipynb](./notebooks/Fulcher_Jesse_HW4.ipynb)
- **Assignment:** [Homework4.pdf](./Homework4.pdf)

## Assignment Questions

> **Note:** Time Series Classification Part 1 was the programming assignment
> for Homework 3 and is not submitted as a new Homework 4 answer. The Homework
> 4 notebook reuses its data loading, train/test splitting, and feature
> extraction code because those features are required below.

## 2. Time Series Classification Part 2: Binary and Multiclass Classification

### 2(a). Binary Classification Using Logistic Regression

#### 2(a)(i). Scatter Plots of Whole-Series Features

Use the training set to classify bending activities versus all other
activities as a binary classification problem. Depict scatter plots of the
three time-domain features selected in Part 1(c)(iv), extracted from time
series 1, 2, and 6 of each instance. Use color to distinguish bending from
the other activities.

#### 2(a)(ii). Scatter Plots After Splitting Each Time Series

Divide each time series in the training set into two approximately equal
parts. Each training instance will then contain 12 time-series segments
instead of 6 time series. Repeat Part 2(a)(i) by depicting scatter plots of
the selected features extracted from both parts of original time series 1, 2,
and 6. Determine whether the results differ considerably from those in Part
2(a)(i).

#### 2(a)(iii). Selecting the Number of Segments and Features

Divide each time series into \(l \in \{1,2,\ldots,20\}\) approximately equal
segments and use time-domain features with logistic regression to solve the
binary classification problem. Dividing a time series changes the number of
features but not the number of instances.

Calculate the p-values of the logistic-regression parameters for each value
of \(l\), prune the features, and refit the model. Alternatively, use backward
selection such as recursive feature elimination (RFE). Use five-fold
cross-validation to select the best pair \((l,p)\), where \(p\) is the number
of features retained by RFE. Explain both the correct and incorrect ways to
perform cross-validation in this setting. Account for class imbalance with
stratified cross-validation if necessary.

#### 2(a)(iv). Training Confusion Matrix, ROC, AUC, and Parameters

Report the training confusion matrix and show the ROC curve and AUC for the
selected classifier. Report the logistic-regression parameters
\(\hat{\beta}_i\) and their associated p-values.

#### 2(a)(v). Test-Set Evaluation

Test the classifier on the test set. Divide each test time series into the
same number of segments selected using the training data, and extract the
test features independently. Compare the test accuracy with the previously
obtained cross-validation accuracy.

#### 2(a)(vi). Separation and Parameter Instability

Determine whether the classes appear sufficiently well separated to cause
instability when calculating the logistic-regression parameters.

#### 2(a)(vii). Case-Control Sampling

Use the confusion matrices to determine whether the classes are imbalanced.
If they are, build a logistic-regression model using case-control sampling,
adjust its parameters, and report the model's confusion matrix, ROC curve,
and AUC.

### 2(b). Binary Classification Using L1-Penalized Logistic Regression

#### 2(b)(i). Selecting \(l\) and the L1 Penalty

Repeat Part 2(a)(iii) using L1-penalized logistic regression. Use L1
regularization for variable selection instead of p-values. Cross-validate
both \(l\), the number of segments per original time series, and
\(\lambda\), the weight of the L1 penalty, or equivalently \(C\), the inverse
regularization budget.

#### 2(b)(ii). Model Comparison

Compare L1-penalized logistic regression with variable selection using
p-values or backward selection. Determine which performs better and which is
easier to implement.

### 2(c). Multiclass Classification

#### 2(c)(i). L1-Penalized Multinomial Logistic Regression

Select the best \(l\) using the same general procedure as in Part 2(b)(i),
then build an L1-penalized multinomial logistic-regression model to classify
all seven activities. Report the test error. Research the definitions of
multiclass confusion matrices and ROC curves, and display them for this
problem when possible.

#### 2(c)(ii). Gaussian and Multinomial Naive Bayes

Repeat Part 2(c)(i) using Naive Bayes classifiers. Use both Gaussian and
Multinomial Naive Bayes and compare their results.

#### 2(c)(iii). Multiclass Model Comparison

Determine which method performs best for multiclass classification in this
problem.

## 3. ISLR 4.8.3

This problem concerns the QDA model, in which observations in each class are
drawn from a normal distribution with a class-specific mean vector and
class-specific covariance matrix. Consider the one-dimensional case
\(p=1\).

Suppose there are \(K\) classes and, for an observation in class \(k\),

\[
X \sim N(\mu_k,\sigma_k^2).
\]

Prove that the Bayes classifier is not linear in this case and argue that it
is quadratic.

> **Hint:** Follow the arguments from Section 4.4.1 without assuming that
> \(\sigma_1^2=\cdots=\sigma_K^2\).

## 4. ISLR 4.8.7

Suppose that we want to predict whether a stock will issue a dividend this
year (`Yes` or `No`) using \(X\), last year's percentage profit. For companies
that issued a dividend, the mean of \(X\) was \(10\); for companies that did
not, the mean was \(0\). The variance of \(X\) in both groups was \(36\), and
80% of companies issued dividends.

Assuming that \(X\) follows a normal distribution, predict the probability
that a company will issue a dividend this year given that its percentage
profit last year was \(X=4\).

> **Hint:** Use the normal density
>
> \[
> f(x)=\frac{1}{\sqrt{2\pi\sigma^2}}
> \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right)
> \]
>
> together with Bayes' theorem.