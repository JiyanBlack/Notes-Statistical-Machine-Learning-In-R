## Q4
#### a
On average, only 10% of the total data is used to make the prediction.
#### b
With 2 predictors, 0.1 * 0.1 = 1% of the total observations are used to make the prediction.
#### c
With 100 preditors, 0.1^98 % is used to make the prediction.
#### d
The drawback of KNN is when p is large, the prediction is less reliable.
#### e
x ^ p = 0.1, x = 0.1^(1/p)

## Q5
#### a
If the Bayes decision boundary is linear, QDA performs better on the training set. LDA is better on the test set.
#### b
If it is non-linear, QDA is better on both testing and training dataset.
#### c
As n increases, the QDA will become more accuracy than LDA. Because QDA has high variance, so is better for large dataset.
#### d
False. Because the assumed model for QDA is wrong, there is no way it could perform better than LDA.

## Q6
#### a
log(p/(1-p)) = -6 + 0.05 * X1 + 1 * X2,  p = 0.3773.
#### b
log(1) = 0 = -6 + 0.05 * X1 + 3.5, X1 = 50.

## Q7
p = 0.75186

## Q8
Logistic Regression. Because the KNN will achieve 0% error rate for training data, so the acctual error rate of KNN is 36%.

## Q9
#### a
p = 0.27
#### b
p = 0.19

## Q10
#### a
There are hardly any pattern in the data.
#### b
```
Deviance Residuals: 
    Min       1Q   Median       3Q      Max  
-1.6949  -1.2565   0.9913   1.0849   1.4579  

Coefficients:
            Estimate Std. Error z value Pr(>|z|)   
(Intercept)  0.26686    0.08593   3.106   0.0019 **
Lag1        -0.04127    0.02641  -1.563   0.1181   
Lag2         0.05844    0.02686   2.175   0.0296 * 
Lag3        -0.01606    0.02666  -0.602   0.5469   
Lag4        -0.02779    0.02646  -1.050   0.2937   
Lag5        -0.01447    0.02638  -0.549   0.5833   
Volume      -0.02274    0.03690  -0.616   0.5377   
---
Signif. codes:  
0 ?**?0.001 ?*?0.01 ??0.05 ??0.1 ??1

(Dispersion parameter for binomial family taken to be 1)

    Null deviance: 1496.2  on 1088  degrees of freedom
Residual deviance: 1486.4  on 1082  degrees of freedom
AIC: 1500.4

Number of Fisher Scoring iterations: 4
```
No predictors seems so important. Only Lag2 seems hold a little impact on the response.

#### c
```
> glm.pred = rep('Down',1089)
> glm.pred[glm.probs>0.5] = 'Up'
> mean(glm.pred == Weekly$Direction)
[1] 0.5610652
> table(glm.pred, Direction)
        Direction
glm.pred Down  Up
    Down   54  48
    Up    430 557
```
The confusion matrix is telling us: Of all true postives, our model can predict most of them, but will also include many false positive.

#### d
```
> glm.pred2 = rep('Down',1089)
> glm.pred2[glm.probs2 > 0.5] = 'Up'
> table(glm.pred2, Direction)
         Direction
glm.pred2 Down  Up
     Down   33  26
     Up    451 579
```
Use only Lag2, we will get a model that tends to predict more postive examples. The True positive and false positive all rises.

#### e
```
> table(lda.class, Direction)
         Direction
lda.class Down  Up
     Down   33  25
     Up    451 580
```
The result of LDA is very close to logistic regression.

#### f
```
> table(qda.pred,Direction)
        Direction
qda.pred Down  Up
    Down    0   0
    Up    484 605
```
QDA achieves better accuray by simple predicting all test data will produce positive result.

#### g
```
knn.fit Down Up
   Down   21 30
   Up     22 31
```

#### h

#### i
