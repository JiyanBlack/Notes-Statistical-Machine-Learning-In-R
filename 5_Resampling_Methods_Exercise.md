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
