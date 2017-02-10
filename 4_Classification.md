# Logistic Regression
* Logistic Regression models the probability that Y belongs to a particular category.
* Use logistic function to give the outputs between 0 and 1.
* odds = p(x)/(1-p(x)), from 0 to infinity. log(odds) = B0+B1*x, log(odds) is logit. Logistic regression has a logit that is linear in X.
* Regression process uses a method called maximum likelihood. Least squares approach is a special case of maximum likelihood.
* Logistic regression has multi-class version, but discriminant analysis is more popular.

# Linear Discriminant Analysis
## Bayes' Theorem
Bayes' theorem gives us a way to calculate conditional probability with prior probability, density function.
## LDA for p=1
* Assumptions are made about the density function f(x) -- normal distribution(Gaussian).
* LDA approximates the Bayes classifier by plugging estimators: πk, μk, σk from the observations.
* πk is estimated by the proportion of the k class in all classes.
## LDA for p>1
* For multiple predictors, use matrix to calculate. 
* Covariance matrix is used to calculate p(x).
## QDA
* QDA hasa covariance matrix for each k-class.
* The function has quadratic x terms. So is called quadratic discriminant analysis.
* More variance and less bias. QDA is much more flexible than LDA.
* QDA is not always better than LDA, should 

# Evaluate the result
* Sensitivity -- the percentage of true postive that are identified.
* Specificity -- the percentage of true negative that are identified.
* Change the threshold will decrease the ovarall accuracy, but may lead to the performance improvement in specific terms.
* ROC curve -- x: false positive rate, y: true positive rate.
* AUC -- Area Under the ROC Curve, the AUC is used to compare diiferent classifiers. Always the larger the better. Because it takes all threshold into account.

# Comparison of Classification Methods
* LDA and logistic regression are closely connected, their logics are all linear function of x. Although they only differ in the fitting procedures, their results are often, but no always the same. The LDA performs better if the Gaussian distribution assumption is correct, much worse is it is far from Gaussian distribution.
* If the decision boundary is highly non-linear, KNN is better than logistic regression and LDA.
* QDA serves a compromise between the KNN and LDA method.
* When observation number is not huge enough, KNN is not a good approach.
* Adding x^2, x^3 ... as predictos in logistic regression or LDA can add variance to the model.
