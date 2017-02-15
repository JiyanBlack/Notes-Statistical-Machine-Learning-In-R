## Q2
#### a
p = 1- 1/n
#### b
p = 1- 1/n
#### c
True. Because for every sample, the probability that it is not jth observation is 1-1/n, so the jth oberservation will not be in the sample is (1-1/n)^n.
#### d
1-(1-1/5)^5 = 0.67232
#### e
1-(1-1/100)^100 = 63.4%
#### f
1-(1-1/10000)^10000 = 63.21%
#### g
It dramatically decreases at the beginning, then stays the same level.
#### h
```
> mean(store)
[1] 0.6418
```
For a sample size of 100, the chance that it will contain a specific sample is roughly 64%

## Q3
a) Randomly divide the observations into k pieces. Each of them is similar size. Select the first piece as the test observation, train the model
from the rest data, test on the first piece, get the test error e1. Select the second, third, fourth ... Kth. Calculate the average value 
of sum(ki)/n  
b) k-fold crossvalidation is better than the validation set approach because it does not depend on the selection of the validation set.  
LOOCV has better performance, but k-fold cross validation requires less computational resource.

## Q4
Use bootstrap, estimate the result through 100 different resampled observations, calculate the std through the final result.

## Q5
#### b-c
```
> fiveB()
[1] 2000
[1] 0.0225

> fiveB()
[1] 4000
[1] 0.02475

> fiveB()
[1] 6000
[1] 0.02616667

> fiveB()
[1] 8000
[1] 0.026
```
With the increase of test dataset, it seems that the error rate is around 2.6%.

#### d
Still around 0.026, no noticeable improvement.

## Q6
#### a
Use logistic regression:
```
Coefficients:
              Estimate Std. Error z value Pr(>|z|)    
(Intercept) -1.154e+01  4.348e-01 -26.545  < 2e-16 ***
income       2.081e-05  4.985e-06   4.174 2.99e-05 ***
balance      5.647e-03  2.274e-04  24.836  < 2e-16 ***
```
bootstrap:
```
         original        bias     std. error
t1* -1.154047e+01  9.699111e-02 4.101121e-01
t2*  2.080898e-05  6.715005e-08 4.127740e-06
t3*  5.647103e-03 -5.733883e-05 2.105660e-04
```
get similar std.error value.

## Q7
#### a
```
> glm.prob =rep(0,1089)

> for(i in 1:1089) {
+   curfit = glm(Direction~Lag1+Lag2, data=Weekly[-i,],family=binomial)
+   glm.prob[i] = predict(curfit, Weekly[i,],type='respon .... [TRUNCATED] 

> glm.pred = rep('Down',1089)

> glm.pred[glm.prob>0.5]='Up'

> glm.err = (glm.pred != Weekly$Direction)
> mean(glm.err)
[1] 0.4499541

```
error rate is 44.995%

## Q8
#### a
n = 100, p = 2  
model : y=x-2 * x^2
#### b
bell shape curve
#### c
```
> error
[1] 5.890979 1.086596 1.102585 1.114772
```
The LOOCV achieves the lowest error at 2 degress of freedom.
#### d
```
> error
[1] 5.890979 1.086596 1.102585 1.114772
```
With another random seed, the value is identical. Because LOOCV will produce exact same result for the same model and data, there is no randomness in this method.
#### e
The model with x and x^2, because the true model is x and x^2, so LOOCV produces the right result.
#### f
```
> for(i in 1:4){
+   glm.fit = glm(y~poly(x,i),data=curdata)
+   print(summary(glm.fit))
+   error[i]=cv.glm(curdata,glm.fit)$delta[1]
+ }

Call:
glm(formula = y ~ poly(x, i), data = curdata)

Deviance Residuals: 
    Min       1Q   Median       3Q      Max  
-7.3469  -0.9275   0.8028   1.5608   4.3974  

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  -1.8277     0.2362  -7.737 9.18e-12 ***
poly(x, i)    2.3164     2.3622   0.981    0.329    
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

(Dispersion parameter for gaussian family taken to be 5.580018)

    Null deviance: 552.21  on 99  degrees of freedom
Residual deviance: 546.84  on 98  degrees of freedom
AIC: 459.69

Number of Fisher Scoring iterations: 2


Call:
glm(formula = y ~ poly(x, i), data = curdata)

Deviance Residuals: 
     Min        1Q    Median        3Q       Max  
-2.89884  -0.53765   0.04135   0.61490   2.73607  

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  -1.8277     0.1032 -17.704   <2e-16 ***
poly(x, i)1   2.3164     1.0324   2.244   0.0271 *  
poly(x, i)2 -21.0586     1.0324 -20.399   <2e-16 ***
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

(Dispersion parameter for gaussian family taken to be 1.06575)

    Null deviance: 552.21  on 99  degrees of freedom
Residual deviance: 103.38  on 97  degrees of freedom
AIC: 295.11

Number of Fisher Scoring iterations: 2


Call:
glm(formula = y ~ poly(x, i), data = curdata)

Deviance Residuals: 
     Min        1Q    Median        3Q       Max  
-2.87250  -0.53881   0.02862   0.59383   2.74350  

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  -1.8277     0.1037 -17.621   <2e-16 ***
poly(x, i)1   2.3164     1.0372   2.233   0.0279 *  
poly(x, i)2 -21.0586     1.0372 -20.302   <2e-16 ***
poly(x, i)3  -0.3048     1.0372  -0.294   0.7695    
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

(Dispersion parameter for gaussian family taken to be 1.075883)

    Null deviance: 552.21  on 99  degrees of freedom
Residual deviance: 103.28  on 96  degrees of freedom
AIC: 297.02

Number of Fisher Scoring iterations: 2


Call:
glm(formula = y ~ poly(x, i), data = curdata)

Deviance Residuals: 
    Min       1Q   Median       3Q      Max  
-2.8914  -0.5244   0.0749   0.5932   2.7796  

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  -1.8277     0.1041 -17.549   <2e-16 ***
poly(x, i)1   2.3164     1.0415   2.224   0.0285 *  
poly(x, i)2 -21.0586     1.0415 -20.220   <2e-16 ***
poly(x, i)3  -0.3048     1.0415  -0.293   0.7704    
poly(x, i)4  -0.4926     1.0415  -0.473   0.6373    
---
Signif. codes:  0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

(Dispersion parameter for gaussian family taken to be 1.084654)

    Null deviance: 552.21  on 99  degrees of freedom
Residual deviance: 103.04  on 95  degrees of freedom
AIC: 298.78

Number of Fisher Scoring iterations: 2
```
  Degrees    statistical_significant  
    1                 B0  
    2                 B0,B1,B2  
    3                 B0,B1,B2  
    4                 B0,B1,B2  

## Q9
#### a
```
> mean(Boston$medv)
[1] 22.53281
```
#### b
```
> sd(medv) / sqrt(dim(Boston)[1])
[1] 0.4088611
```
The standard error of sample mean is 0.40886
#### c
```
Bootstrap Statistics :
    original       bias    std. error
t1* 22.53281 -0.004750198   0.3920971
```
The bootstrap std error is 0.392, close to 0.40886
#### d
95% confidence interval:
```
> conf[1] = (medv.mean - 2*medv.std)

> conf[2] = (medv.mean + 2*medv.std)
> conf
[1] 21.71508 23.35053
```
#### e
```
> median(medv)
[1] 21.2
```
#### f
```
Call:
boot(data = Boston, statistic = boot.median, R = 1000)


Bootstrap Statistics :
    original   bias    std. error
t1*     21.2 -0.01565   0.3897428
```
std.error for median is 0.3897

#### g
quantile estimate is ```  10%   12.75 ```
#### h
```
boot(data = Boston, statistic = boot.10, R = 1000)


Bootstrap Statistics :
    original  bias    std. error
t1*    12.75  0.0152   0.5069082
```
std error for 10 percentile of medv is 0.5069
