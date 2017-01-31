
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
  
