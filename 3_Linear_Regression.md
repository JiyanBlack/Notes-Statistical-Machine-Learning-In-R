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

## Q8
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

> predict(my_fit, data.frame(horsepower=98))
       1 
24.46708 
```
1. 
  a. there is a relationship betweem X and Y, F-statistic: 599.7, p-value ~= 0
  b. The relationship is very strong, p-value is very small.
  c. is negative, the estimated value is -0.158
  d. The predicted value is: 24.47
2. 
```r
plot(Auto$horsepower, Auto$mpg)
abline(my_fit)
```
3.
```r
par(mfrow=c(2,2))
plot(my_fit)
```
Problems:
* residual plot is not random normal distribution
* many high leverage points

## Q9
```
cor(subset(Auto, select=-name))
                    mpg  cylinders displacement horsepower     weight acceleration       year     origin
mpg           1.0000000 -0.7776175   -0.8051269 -0.7784268 -0.8322442    0.4233285  0.5805410  0.5652088
cylinders    -0.7776175  1.0000000    0.9508233  0.8429834  0.8975273   -0.5046834 -0.3456474 -0.5689316
displacement -0.8051269  0.9508233    1.0000000  0.8972570  0.9329944   -0.5438005 -0.3698552 -0.6145351
horsepower   -0.7784268  0.8429834    0.8972570  1.0000000  0.8645377   -0.6891955 -0.4163615 -0.4551715
weight       -0.8322442  0.8975273    0.9329944  0.8645377  1.0000000   -0.4168392 -0.3091199 -0.5850054
acceleration  0.4233285 -0.5046834   -0.5438005 -0.6891955 -0.4168392    1.0000000  0.2903161  0.2127458
year          0.5805410 -0.3456474   -0.3698552 -0.4163615 -0.3091199    0.2903161  1.0000000  0.1815277
origin        0.5652088 -0.5689316   -0.6145351 -0.4551715 -0.5850054    0.2127458  0.1815277  1.0000000
```

```
> q9_fit = lm(mpg~ .-name, data =Auto)
> summary(q9_fit)

Call:
lm(formula = mpg ~ . - name, data = Auto)

Residuals:
    Min      1Q  Median      3Q     Max 
-9.5903 -2.1565 -0.1169  1.8690 13.0604 

Coefficients:
               Estimate Std. Error t value Pr(>|t|)    
(Intercept)  -17.218435   4.644294  -3.707  0.00024 ***
cylinders     -0.493376   0.323282  -1.526  0.12780    
displacement   0.019896   0.007515   2.647  0.00844 ** 
horsepower    -0.016951   0.013787  -1.230  0.21963    
weight        -0.006474   0.000652  -9.929  < 2e-16 ***
acceleration   0.080576   0.098845   0.815  0.41548    
year           0.750773   0.050973  14.729  < 2e-16 ***
origin         1.426141   0.278136   5.127 4.67e-07 ***
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

Residual standard error: 3.328 on 384 degrees of freedom
Multiple R-squared:  0.8215,	Adjusted R-squared:  0.8182 
F-statistic: 252.4 on 7 and 384 DF,  p-value: < 2.2e-16
```
1. There is relationship between predictors and response. (F-statistic and its p-value)
2. weight,year and origin all have significant relationship to the response.
3. it suggest that with the increasing of year, the car costs more gas.
4. residual plot display high residual points, and it has non-random pattern. Also point 14 has high leverage.
5. the interaction term weight:year has significant impact. 
```
Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept) -1.120e+02  2.077e+01  -5.394 1.20e-07 ***
weight       2.674e-02  5.228e-03   5.116 4.93e-07 ***
year         2.021e+00  2.731e-01   7.399 8.67e-13 ***
origin       2.354e+00  5.115e+00   0.460    0.646    
weight:year -4.401e-04  6.968e-05  -6.316 7.38e-10 ***
year:origin -1.863e-02  6.624e-02  -0.281    0.779    
```
## Q10
```
Residuals:
    Min      1Q  Median      3Q     Max 
-6.9206 -1.6220 -0.0564  1.5786  7.0581 

Coefficients:
             Estimate Std. Error t value Pr(>|t|)    
(Intercept) 13.043469   0.651012  20.036  < 2e-16 ***
Price       -0.054459   0.005242 -10.389  < 2e-16 ***
UrbanYes    -0.021916   0.271650  -0.081    0.936    
USYes        1.200573   0.259042   4.635 4.86e-06 ***
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

Residual standard error: 2.472 on 396 degrees of freedom
Multiple R-squared:  0.2393,	Adjusted R-squared:  0.2335 
F-statistic: 41.52 on 3 and 396 DF,  p-value: < 2.2e-16
```
* Price has negative effect on sales as well as Urban. US produced cars are more welcome.
* y = 13.043 - 0.054 * price - 0.022 * UrbanYes + 1.201 * USYes
* We can only reject H0 for Price and US.
```
Residuals:
    Min      1Q  Median      3Q     Max 
-6.9269 -1.6286 -0.0574  1.5766  7.0515 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) 13.03079    0.63098  20.652  < 2e-16 ***
Price       -0.05448    0.00523 -10.416  < 2e-16 ***
USYes        1.19964    0.25846   4.641 4.71e-06 ***
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

Residual standard error: 2.469 on 397 degrees of freedom
Multiple R-squared:  0.2393,	Adjusted R-squared:  0.2354 
F-statistic: 62.43 on 2 and 397 DF,  p-value: < 2.2e-16
```
* The latter model that eliminates Urban predictor is better because it has larger F-statistic without compromise R2.
* Confidence Interval:
```
                  2.5 %      97.5 %
(Intercept) 11.79032020 14.27126531
Price       -0.06475984 -0.04419543
USYes        0.69151957  1.70776632
```
* According to the studentized residual plot, no points exceed 3. But there are several high leverage points in the summary graph.

## Q11
1. linear regression result:
```
Residuals:
    Min      1Q  Median      3Q     Max 
-1.9154 -0.6472 -0.1771  0.5056  2.3109 

Coefficients:
  Estimate Std. Error t value Pr(>|t|)    
x   1.9939     0.1065   18.73   <2e-16 ***
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

Residual standard error: 0.9586 on 99 degrees of freedom
Multiple R-squared:  0.7798,	Adjusted R-squared:  0.7776 
F-statistic: 350.7 on 1 and 99 DF,  p-value: < 2.2e-16
```
The x is significant and the R-squared value is 0.77 means that 77% of variance in Y can be explained by X.

2. 
```
Residuals:
    Min      1Q  Median      3Q     Max 
-0.8699 -0.2368  0.1030  0.2858  0.8938 

Coefficients:
  Estimate Std. Error t value Pr(>|t|)    
y  0.39111    0.02089   18.73   <2e-16 ***
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

Residual standard error: 0.4246 on 99 degrees of freedom
Multiple R-squared:  0.7798,	Adjusted R-squared:  0.7776 
F-statistic: 350.7 on 1 and 99 DF,  p-value: < 2.2e-16
```
The y is statistically significant. Reject null hypothesis.

3. The x~y and y~x in 1 and 2 share common R-value, but the estimated intercept is different.
4. Test:
```r
top <- sqrt(100-1) * sum(x*y)
down <- sqrt(sum(x*x)*sum(y*y) - sum(x*y)^2)
print(top/down)
```
get:
```
> print(top/down)
[1] 18.72593
```
Same as the t-value in regression.
5. The x and y's role does not matter because the equation of T-statistic is the same for x~y and y~x.

## Q12
1. When the true relationship between x and y are 1.
2. 
```
> x = rnorm(1000)
> y = 2*x + rnorm(1000)
> fit = lm(y~x+0)
> summary(fit)

Call:
lm(formula = y ~ x + 0)

Residuals:
    Min      1Q  Median      3Q     Max 
-3.3010 -0.6850 -0.0518  0.7375  3.5917 

Coefficients:
  Estimate Std. Error t value Pr(>|t|)    
x  2.02695    0.03172   63.91   <2e-16 ***
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

Residual standard error: 1.053 on 999 degrees of freedom
Multiple R-squared:  0.8035,	Adjusted R-squared:  0.8033 
F-statistic:  4085 on 1 and 999 DF,  p-value: < 2.2e-16

> fit_reverse = lm(x~y+0)
> summary(fit_reverse)

Call:
lm(formula = x ~ y + 0)

Residuals:
     Min       1Q   Median       3Q      Max 
-1.33439 -0.30657 -0.00058  0.31087  1.65686 

Coefficients:
  Estimate Std. Error t value Pr(>|t|)    
y 0.396403   0.006202   63.91   <2e-16 ***
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

Residual standard error: 0.4655 on 999 degrees of freedom
Multiple R-squared:  0.8035,	Adjusted R-squared:  0.8033 
F-statistic:  4085 on 1 and 999 DF,  p-value: < 2.2e-16
```
## Q13
3. The length of y is 100. B0 = -1, B1 = 0.5.
4. 
```
Residuals:
     Min       1Q   Median       3Q      Max 
-0.60032 -0.15270 -0.00523  0.16077  0.48807 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) -0.98497    0.02303  -42.77   <2e-16 ***
x            0.48626    0.02395   20.31   <2e-16 ***
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

Residual standard error: 0.2291 on 98 degrees of freedom
Multiple R-squared:  0.808,	Adjusted R-squared:  0.806 
F-statistic: 412.4 on 1 and 98 DF,  p-value: < 2.2e-16
```
The estimated value of intercept and B1 is -0.98 and 0.486, close to true value but still different.
5.
```
> fit_sqr = lm(y~x+I(x^2))
> summary(fit_sqr)

Call:
lm(formula = y ~ x + I(x^2))

Residuals:
     Min       1Q   Median       3Q      Max 
-0.58409 -0.15274 -0.01265  0.16004  0.48103 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) -0.96466    0.02992 -32.245   <2e-16 ***
x            0.48089    0.02446  19.660   <2e-16 ***
I(x^2)      -0.02252    0.02120  -1.062    0.291    
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

Residual standard error: 0.229 on 97 degrees of freedom
Multiple R-squared:  0.8102,	Adjusted R-squared:  0.8063 
F-statistic:   207 on 2 and 97 DF,  p-value: < 2.2e-16
```
Accept null hypothesis for x^2 term, p-value too small. R-squared value is not improved.

## Q14
1. coefficients: 2,2,0.3
2. 
```
> cor(x1,x2)
[1] 0.8181009
```
The correlation between x1 and x2 is 0.8181009
3. 
```
> fit = lm(y~x1+x2)
> summary(fit)

Call:
lm(formula = y ~ x1 + x2)

Residuals:
     Min       1Q   Median       3Q      Max 
-2.93415 -0.44932  0.00685  0.65498  2.62138 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)   2.0113     0.2253   8.925  2.8e-14 ***
x1            2.2993     0.6710   3.427 0.000897 ***
x2           -0.2352     1.0949  -0.215 0.830368    
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

Residual standard error: 1.044 on 97 degrees of freedom
Multiple R-squared:  0.2481,	Adjusted R-squared:  0.2326 
F-statistic:    16 on 2 and 97 DF,  p-value: 9.86e-07
```
Reject the null hypothesis for x1, p-value small. But cannot reject for x2. x2 is insignificant.
4. 
```
Residuals:
     Min       1Q   Median       3Q      Max 
-2.92132 -0.45811 -0.01036  0.64112  2.62227 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)   2.0123     0.2242   8.976 2.02e-14 ***
x1            2.1813     0.3840   5.681 1.37e-07 ***
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

Residual standard error: 1.038 on 98 degrees of freedom
Multiple R-squared:  0.2477,	Adjusted R-squared:  0.2401 
F-statistic: 32.27 on 1 and 98 DF,  p-value: 1.374e-07
```
Reject H0 of x1, x1 becomes statistically significant.
5.
```
Call:
lm(formula = y ~ x2)

Residuals:
     Min       1Q   Median       3Q      Max 
-3.10165 -0.76917  0.07393  0.67426  2.53705 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)   2.4185     0.2017  11.991  < 2e-16 ***
x2            2.8344     0.6633   4.273 4.47e-05 ***
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

Residual standard error: 1.099 on 98 degrees of freedom
Multiple R-squared:  0.1571,	Adjusted R-squared:  0.1485 
F-statistic: 18.26 on 1 and 98 DF,  p-value: 4.468e-05
```
Reject H0 for x2, x2 is statistically significant.
6. No. Because x1 and x2 are strongly correlated, so if x1 and x2 all participate in the regression, it is possible that one of its significant will be mitigated.
