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
