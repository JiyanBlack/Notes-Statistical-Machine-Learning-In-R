
# Introduction to R
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
* plot(x,y, xlab="x label",ylab="y label", main="sample graph")
* generate pdf:
```r
pdf('filename.pdf')
plot(x,y,col='green')
dev.off()
```
