# Simple Linear Regression

## Least Squares Method
* Most common method.
* Difference between y and y(predict) is called residual
* Residual sum of squares(RSS) is the sum of squared residuals
* Least Squares Approach aims to choose parameters that minimize RSS.

## Assesing the accuracy of coefficients estimates
* Population Regression Line: the deal best approximation to the true relationship between X and Y.
* Least Squares Line: the actual approximation produced by least squares method.
* Bias/unbiased estimator: an unbiased term does not systematically over-or-under-estimate the true parameter.
* Standard Error: The standard error (SE) is the standard deviation of the sampling distribution of a statistic, most commonly of the mean.
* Residual Standard Error: RSE = sqrt(RSS/(n-2))
* 95% Confidence interval: 95% that this range will contain the true value.
* 95% confidence interval = [estimator - 2SE,estimator + 2SE]
* Hypothesis Tests: null hyphothesis(H0) and alternative hypothesis(Ha)
* To reject/admit H0, we need to know that beta is 0 or not. It depends on the error of different samples. So SE(beta) also matters a lot.
* t-statistic is used to reject/admin H0: t = (beta-0) / SE(beta)
* the t-statistic has a t-distribution with n-2 degrees of freedom. 
* t-distribution is similar to normal distribution when n>30.
* p-value: get the x according to t-statistic from the t-distribution. A small p-value indicates that it is unlikely to observe such a substantial association between the predictor and the response due to chance, in the absence of any real association between the predictor and the response.
* p-value < T(t-statistic), reject null hypothesis, there is a correlation between x and y.

## Assessing the accuracy of the model
* After rejecting the null hypothesis, we want to know how well our data is fitting. Two main terms: Residual Standard Error(RSE) and R^2 statistic.
#### RSE
* RSE = sqrt(RSS / n-1-p), RSS = sum((y_predict - y)^2)
* RSE is a measure of the lack of fit of the model to the data, it is an absolute measurement, hava not uniform standard on different datasets.

#### R<sup>2</sup>
* R squared is a relative measurement -- the proportion of variance in Y explained by predictors,it is in [0,1] and independent of X's scale.
* R<sup>2</sup> = (TSS-RSS) / TSS = 1- RSS/TSS, TSS = sum((y_predict - y_mean)^2)
* R squared statistic has an interpretational advantage over RSE.
* R<sup>2</sup> and the correlation are both the measure of linear relationship between X and Y. In simple linear regression fitting, R<sup>2</sup> = r<sup>2</sup>(correlation squared)
* correlation does not extend to multiple variable regression, instead we use R<sup>2</sup>.

# Multiple Linear Regression
## Estimating the Regression Coefficients
#### F statistic
* F-statistic is used to test whether at least one variable contribute to the variance in Y.
* F = ((TSS - RSS)/p) / (RSS/(n - p -1)) , p is the number of predictors.
* Given the value of p and n, we can compute the p-value associated with F statistic.
* If F is close to 1, H0 is true. F >> 1, then Ha is true.

## Variable Selection
* Forward selection: begin with null model(0 variables), try out the p selection and add the variable that results the lowest RSS.
* Backward selection: Start with all variables fitted in the model, and remove the variable with the lagest p-value.
* Mixed selection: Start with no variables, add the variable that result in the smallest RSS, and then test if any p-value changing, remove variables with large p-value.

## Evaluate Model
* R<sup>2</sup> and RSE
* Confidence Interval: the Y_predict is different from the true population regression plane. This is due called reducible error. Confidence Interval is used to compute how close Y_predict is close to population regression.
* Prediction Intervals: even if we have the true population regression, there is still difference between the observations and the regression due to irreducible error. Prediction intervals are used to answer how much Y_true vary from Y.
* Given the x1 and x2, we predict 95% confidence interval of y is [98,102], means that 95% this range will contain true population regression result. The prediction interval is [90,110], means that 95% this range will contain the true Y value in real observation.

# Other Considerations

## Qualitative Predictors
* Vectorize the predictors
  * Predictors with two levels: 0 - male, 1 - female
  * Predictors with more levels: create more dummy variables, x1 -- asian or not, x2 -- white or not.

## Extensions of the Linear Model
#### Additive Assumption
* Additive: the changing in a predictor Xi on Y is independent of other predictors.
* Add interaction terms: X1, X2, X1*X2
#### Linear Assumption
* Add polynomial terms

## Potential Problems
* Non-linearity of the response-predictor relationships: residual plot -- plot the residuals versus the predicted values Y. Should display normal random distribution. Use non-linear transformations on the predictors.
* Correlation of Error Terms: produce unwarranted sense of confidence in our model.
* Non-constant Variance of Error Terms: the Y - residual plot may display a funnel shape. Transform Y such as logY. 
* Outliers: yi is far from the predicted value y(i): usually have no huge impact on the regression result, but have impact on the RSE and R<sup>2</sup>. Residual Plots can identify outliers. But Studentized Residuals is more convenient, Studentized Residuals are relative values, >3 means possible outliers.
* High leverage Points: unusual value for x, the predicted y seems normal. These points have high impact on the final regression due to the extreme x value. Leverage Statistic displays the high leveral points.
* Collinearity: means two or more predictors are strongly dependent. Collinearity reduces the accuracy of the estimates of the coefficients and confuse which predictor is useful(change p-value), the power of the hypothesis test is reduced. Compute the Variance Inflation Factor(VIF) to detect the collinearity. When VIF is close to 1, it means that it has no collinearity. If the collinearity is detected, we can drop all but one predictor or combine them together.

# Summary
* Is there a relationship between predictors and results? Using F-statistic to decide whether or not reject null hypothesis.
* How strong is the relationship? RSE and R<sup>2</sup>
* which predictors matter? calculate the p-value for each variable's F-statistic. Variable selection problem.
* How accuarately can we predict? Y = f(X) + residual, if evaluate f(X), we use confidence interval, if Y we use prediction interval.
* Is the relationship linear? Variable Transformation.
* Is there synergy among predictors? Small p-value for the interaction terms indicates the presence of such relationship.

# Compare with K-nearest Neighbours
* Non-parametric method -- KNN has advantages:
 1. Do not assume the form of the function.
 2. More flexible, work for any case.
* The parametric approach will outperform the non-parametric approach if the parametric form that has been selected is close to the truth form.
* The selection of K is a bias-variance tradeoff.
* The increase in dimension has only caused a small deterioration in the regression method, but affect the KNN a lot.
* Parametric will outperform a non-parametric method when there is a small number of observations per predictor.

# Exercises
## Q3
Y = 50 + 20* GPA + 0.07 * IQ + 35 * Gender + 0.01 * GPA:IQ - 10 * GPA:Gender
1. iii is correct, because (35 - 10GPA) is the term before Gender, so if GPA is high, males earn more than females.
2. 137.1
3. False. The value of coefficient has nothing to do with the importance of that variable. Should check the p-value.

## Q4
1. Although the true relationship is linear, the cubic regression has smaller RSS. Because there will be irreducible errors in data, and cubic regression will try to reduce the error caused by them. The linear regression will not instead.
2. For test RSS, linear regression will have smaller RSS. Because the true relationship is linear, the cubic regression will perform badly on non-training data since it's form is not linear.
3. Polynomial regression will always have lower training RSS than linear model.
4. There is not enough information. When the true form is far from linear, cubic model wins, vice versa.

## Q6
True, having x=x_ba, y = y_ba, and do some calculas.

## Q7
```
> my_fit = lm(mpg~ horsepower, data = Auto)

> summary(my_fit)

Call:
lm(formula = mpg ~ horsepower, data = Auto)

Residuals:
     Min       1Q   Median       3Q      Max 
-13.5710  -3.2592  -0.3435   2.7630  16.9240 

Coefficients:
             Estimate Std. Error t value Pr(>|t|)    
(Intercept) 39.935861   0.717499   55.66   <2e-16 ***
horsepower  -0.157845   0.006446  -24.49   <2e-16 ***
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

Residual standard error: 4.906 on 390 degrees of freedom
Multiple R-squared:  0.6059,	Adjusted R-squared:  0.6049 
F-statistic: 599.7 on 1 and 390 DF,  p-value: < 2.2e-16
```
