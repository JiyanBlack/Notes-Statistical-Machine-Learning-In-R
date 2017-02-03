
# Introduction to R

## Matrix and Indices
* Create vector: a = c(1,2,3,4,5) or a <- 1:5
* length(a) --> length of vector / num of elements in matrix
* ls() --> list all objects in memory
* rm(x), rm(list=ls()) --> remove objects x, remove all objects
* help: ?funcname
* create matrix: matrix(data=1:100, nrow=10, ncol=10, byrow=T)
* rnorm() --> generates a vector of random normal variables
* cor(x,y) --> the statistical correlation between x and y
* set.seed(num) --> set random seed to a particular value, rnorm will always generate the same vector every time.
* mean(vector), var(vector), sd(vector) --> the mean, variance, standard deviation of the vector
* seq(a,b length=n) --> create an vector from a to b, length is n
* outer(x,y,function) --> perform the function to generate a outer join matrix
* A = matrix(1:16,4,4), A[2,3], A[1:3,2:4], A[1:2,], A[,1:4]
* A[-1:2,] --> negative value means detele the cooresponding row
* rep(value,rownumber) --> produce repreat value vector.

## Ploting data
* plot(x,y, xlab="x label",ylab="y label", main="sample graph")
* generate pdf:
```r
pdf('filename.pdf')
plot(x,y,col='green')
dev.off()
```
* contour(x,y,z, nlevels=45) --> contour plot
* image(x,y,f) --> heat map
* persp(x,y,z,theta=15,phi=15) --> 3d plot
* plot(Dataframe$column1, Dataframe$column2) --> selecting columns
* hist(singleVector, col='red',breaks=15) --> draw histogram

## Loading Data
* Auto = read.table('relative path', header=T) --> read a file into a dataframe
* fix(Auto) --> display data in a new window
* names(Auto) --> display column names
* attach(Auto) --> attach auto's columns to the name space
* cylinders = as.factor(cylinders) --> convert quantitative values to the qualitative values
* summary(Auto), summary(mpg) --> produce a summary of the data.
* rownames(dt_variable) = dt_variable[,1] --> set the row name as the first column, do not take part in the data processing.


# Exercises
1. Q1:
  a. flexble statistical learning method is better.
  b. inflexible method.
  c. flexible method.
  d. inflexible.
2. Q2:
  a. regression, inference
  b. classification, prediction
  c. regression, prediction
3. Q3:
  variance: increase, more flexibility, more changes for different datasets, more variance
  bias: decrease
  Bayes error: constant
  training error: decrease, as more flexibility always fits better
  test error: u-shape, sum of bias, variance and Bayes.
4. Q4:
    * for each commercial item, predict whether its going to be sold out or not.
    * predict whether a human has some disease.
    * predict that whether a stock is worth buying or not.
5. Q5:
  1. Flexible method: can fit to more complex data, more accurate for training data. But overfitting and data intepretation are the main issues for flexible method. When we have few data but many features, or we want to inteprete data, we may do not want a flexible method.

6. Q6: parametric: before learning, the form of f needs to be specified by human. Non-parametric: generate paras by machine.  
Parametric: need less data, can be intepreted. Non-parametric: can produce more accurate fit if data are enough.

7. Q7:   
  a. 3,2,sqrt(10),sqrt(5),sqrt(2),sqrt(3)  
  b. Green, sqrt(2) is smallest  
  c. 2,sqrt(2),sqrt(3) are the three nearest neighbours, is red,green,red, so the result is red.  
  d. small, because small k value will produce more complex boundaries.  

8. Q8:
```r
#8
summary(college)

pairs(college[,1:10])

attach(college)
Private = as.factor(Private)
plot(Private,Outstate)

Elite = rep('No',nrow(college))
Elite[Top10perc > 50] = 'Yes'
Elite = as.factor(Elite)
college = data.frame(college,Elite)
summary(Elite)
plot(Elite,Outstate)

hist(Apps, breaks = 100)
hist(Accept, breaks = 100)
hist(Enroll, breaks = 100)
hist(Accept/Apps, breaks = 100)

```

9. Q9
  1. quantitative: mpg,displacement,horsepower,weight,acceleration; qualitative: cylinders, year, origin, name
  2.
  ```
  mpg          cylinders      displacement  
 Min.   : 9.00   Min.   :3.000   Min.   : 68.0  
 1st Qu.:17.50   1st Qu.:4.000   1st Qu.:104.0  
 Median :23.00   Median :4.000   Median :146.0  
 Mean   :23.52   Mean   :5.458   Mean   :193.5  
 3rd Qu.:29.00   3rd Qu.:8.000   3rd Qu.:262.0  
 Max.   :46.60   Max.   :8.000   Max.   :455.0  
                                                
   horsepower        weight      acceleration  
 Min.   : 46.0   Min.   :1613   Min.   : 8.00  
 1st Qu.: 75.0   1st Qu.:2223   1st Qu.:13.80  
 Median : 93.5   Median :2800   Median :15.50  
 Mean   :104.5   Mean   :2970   Mean   :15.56  
 3rd Qu.:126.0   3rd Qu.:3609   3rd Qu.:17.10  
 Max.   :230.0   Max.   :5140   Max.   :24.80  
 NA's   :5
 ```
  4.
  ```
  mpg          cylinders      displacement
 Min.   :11.00   Min.   :3.000   Min.   : 68  
 1st Qu.:18.00   1st Qu.:4.000   1st Qu.:100  
 Median :23.90   Median :4.000   Median :145  
 Mean   :24.44   Mean   :5.371   Mean   :187  
 3rd Qu.:30.70   3rd Qu.:6.000   3rd Qu.:250  
 Max.   :46.60   Max.   :8.000   Max.   :455  
                                              
   horsepower      weight      acceleration  
 Min.   : 46   Min.   :1649   Min.   : 8.50  
 1st Qu.: 75   1st Qu.:2215   1st Qu.:14.00  
 Median : 90   Median :2795   Median :15.50  
 Mean   :101   Mean   :2934   Mean   :15.72  
 3rd Qu.:115   3rd Qu.:3504   3rd Qu.:17.30  
 Max.   :230   Max.   :4997   Max.   :24.80  
 ```
 6. To predict mpg, the weight, acceleration, horsepower,cylinders are very important. Because through the
 plot, we can see that mpg has negative correlations with horsepower, weight, has positive relationship with
 acceleration.
 
