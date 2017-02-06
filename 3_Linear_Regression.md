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
* RSE = sqrt(RSS / n-2), RSS = sum((y_predict - y)^2)
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
