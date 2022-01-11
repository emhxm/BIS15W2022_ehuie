---
title: "Lab 2 Homework"
author: "Emily Huie"
date: "1/9/22"
output:
  html_document: 
    theme: spacelab
    keep_md: yes
---

## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove the `#` for the included code chunks to run. Be sure to add your name to the author header above.  

Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!  

1. What is a vector in R? 
A vector contains values of the same type (e.g. integers, characters). In order to create a vector, we use the c command which stands for "concatenate". 
An example would be:

```r
favorite_fruit <- c("strawberry","mango","watermelon","raspberry","kiwi")
favorite_fruit
```

```
## [1] "strawberry" "mango"      "watermelon" "raspberry"  "kiwi"
```


2. What is a data matrix in R?  
A data matrix is like a table, where it compiles multiple vectors. 
An example would be the following where I created a data matrix that compares store prices of fruit (Safeway vs. Trader Joe's).
(In my draft version, I had print values, for this final version I only printed the final matrix :D ),

```r
#ComparingStorePrices
Strawberry <-c(2, 1.5)
Mango <- c(3, 2)
Watermelon <-c(2, 1)
fruit <-c(Strawberry, Mango, Watermelon)
fruit_matrix <-matrix(fruit, nrow=3, byrow=T)
store_name <-c("Safeway", "Trader Joe's")
fruit_name <-c("Strawberry","Mango","Watermelon")
colnames(fruit_matrix)<- store_name
rownames(fruit_matrix)<- fruit_name
fruit_matrix
```

```
##            Safeway Trader Joe's
## Strawberry       2          1.5
## Mango            3          2.0
## Watermelon       2          1.0
```

3. Below are data collected by three scientists (Jill, Steve, Susan in order) measuring temperatures of eight hot springs. Run this code chunk to create the vectors.  

```r
spring_1 <- c(36.25, 35.40, 35.30)
spring_2 <- c(35.15, 35.35, 33.35)
spring_3 <- c(30.70, 29.65, 29.20)
spring_4 <- c(39.70, 40.05, 38.65)
spring_5 <- c(31.85, 31.40, 29.30)
spring_6 <- c(30.20, 30.65, 29.75)
spring_7 <- c(32.90, 32.50, 32.80)
spring_8 <- c(36.80, 36.45, 33.15)
```

4. Build a data matrix that has the springs as rows and the columns as scientists.  


```r
#1 Combine the 8 springs into one vector.
springs <-c(spring_1, spring_2, spring_3, spring_4, spring_5, spring_6, spring_7, spring_8)
springs
```

```
##  [1] 36.25 35.40 35.30 35.15 35.35 33.35 30.70 29.65 29.20 39.70 40.05 38.65
## [13] 31.85 31.40 29.30 30.20 30.65 29.75 32.90 32.50 32.80 36.80 36.45 33.15
```

```r
#2 Create a matrix
springs_matrix <- matrix(springs, nrow=8, byrow=T)
springs_matrix
```

```
##       [,1]  [,2]  [,3]
## [1,] 36.25 35.40 35.30
## [2,] 35.15 35.35 33.35
## [3,] 30.70 29.65 29.20
## [4,] 39.70 40.05 38.65
## [5,] 31.85 31.40 29.30
## [6,] 30.20 30.65 29.75
## [7,] 32.90 32.50 32.80
## [8,] 36.80 36.45 33.15
```


```r
#Assign column and row names
scientists <-c("Jill","Steven","Susan")
spring_names<-c("Bluebell Spring","Opal Spring","Riverside Spring","Too Hot Spring", "Mystery Spring", "Emerald Spring", "Black Spring", "Pearl Spring")
```

5. The names of the springs are 1.Bluebell Spring, 2.Opal Spring, 3.Riverside Spring, 4.Too Hot Spring, 5.Mystery Spring, 6.Emerald Spring, 7.Black Spring, 8.Pearl Spring. Name the rows and columns in the data matrix. Start by making two new vectors with the names, then use `colnames()` and `rownames()` to name the columns and rows.

```r
#Name the rows and columns of data matrix
colnames(springs_matrix)<-scientists
rownames(springs_matrix)<-spring_names

#Final Matrix
springs_matrix
```

```
##                   Jill Steven Susan
## Bluebell Spring  36.25  35.40 35.30
## Opal Spring      35.15  35.35 33.35
## Riverside Spring 30.70  29.65 29.20
## Too Hot Spring   39.70  40.05 38.65
## Mystery Spring   31.85  31.40 29.30
## Emerald Spring   30.20  30.65 29.75
## Black Spring     32.90  32.50 32.80
## Pearl Spring     36.80  36.45 33.15
```


6. Calculate the mean temperature of all eight springs.

```r
#Calculated mean temperature for each spring
bluebellspringmean <-mean(springs_matrix[1,])
opalspringmean<-mean(springs_matrix[2,])
riversidespringmean<-mean(springs_matrix[3,])
toohotspringmean<-mean(springs_matrix[4,])
mysteryspringmean<-mean(springs_matrix[5,])
emeraldspringmean<-mean(springs_matrix[6,])
blackspringmean<-mean(springs_matrix[7,])
pearlspringmean<-mean(springs_matrix[8,])
#Combined mean values into one vector
mean_values<-c(bluebellspringmean,opalspringmean,riversidespringmean, toohotspringmean, mysteryspringmean,emeraldspringmean,blackspringmean,pearlspringmean)
mean_values
```

```
## [1] 35.65000 34.61667 29.85000 39.46667 30.85000 30.20000 32.73333 35.46667
```

7. Add this as a new column in the data matrix.

```r
#Added mean values as a new column
added_mean_springs_matrix <-cbind(springs_matrix,mean_values)
added_mean_springs_matrix
```

```
##                   Jill Steven Susan mean_values
## Bluebell Spring  36.25  35.40 35.30    35.65000
## Opal Spring      35.15  35.35 33.35    34.61667
## Riverside Spring 30.70  29.65 29.20    29.85000
## Too Hot Spring   39.70  40.05 38.65    39.46667
## Mystery Spring   31.85  31.40 29.30    30.85000
## Emerald Spring   30.20  30.65 29.75    30.20000
## Black Spring     32.90  32.50 32.80    32.73333
## Pearl Spring     36.80  36.45 33.15    35.46667
```



8. Show Susan's value for Opal Spring only.

```r
#Susan column 3 and Opal Srping in Row 2, therefore [row,column] = [2,3]
added_mean_springs_matrix[2,3]
```

```
## [1] 33.35
```


9. Calculate the mean for Jill's column only. 
#Jill's Column = Column 1 

```r
added_mean_springs_matrix[,1]
```

```
##  Bluebell Spring      Opal Spring Riverside Spring   Too Hot Spring 
##            36.25            35.15            30.70            39.70 
##   Mystery Spring   Emerald Spring     Black Spring     Pearl Spring 
##            31.85            30.20            32.90            36.80
```

```r
mean(added_mean_springs_matrix[,1])
```

```
## [1] 34.19375
```

10. Use the data matrix to perform one calculation or operation of your interest.

Manual Ranking of Mean Spring Temperatures (without Rank Function):
Identified the column of data matrix that contains mean values. Found the maximum mean value by using max function. Then, I found the 2nd highest number by first creating a vector that inlcudes all the values that are less than my highest number, then using the max function to find the highest number of this vector which would represent the 2nd highest mean value. I repeat this process until I rank the mean values from 1 to 8. Then, I assigned the values to the spring name they correspond with and created a table to illustrate the ranked mean value of the springs from high to low. 
One struggle I had was figuring out if there was a way I did not have to reassign the names of the springs and if the mean values could already be associated with their respective spring. I was unable to figure out this problem and instead, manually matched the names of the springs with my mean values.  

```r
#Finding mean values or I can use my already created mean_values vector. 
added_mean_springs_matrix[,4]
```

```
##  Bluebell Spring      Opal Spring Riverside Spring   Too Hot Spring 
##         35.65000         34.61667         29.85000         39.46667 
##   Mystery Spring   Emerald Spring     Black Spring     Pearl Spring 
##         30.85000         30.20000         32.73333         35.46667
```



```r
#Ranking mean values from highest to lowest which is represented by number# where # equals the ranking order where 1 is highest and 8 is lowest.  
number1<-max(added_mean_springs_matrix[,4])
number2<-max(mean_values[mean_values<number1])
number3<-max(mean_values[mean_values<number2])
number4<-max(mean_values[mean_values<number3])
number5<-max(mean_values[mean_values<number4])
number6<-max(mean_values[mean_values<number5])
number7<-max(mean_values[mean_values<number6])
number8<-max(mean_values[mean_values<number7])
ranked_springs_values<-c(number1,number2,number3,number4,number5,number6,number7,number8)
ranked_springs_values
```

```
## [1] 39.46667 35.65000 35.46667 34.61667 32.73333 30.85000 30.20000 29.85000
```



```r
#Created matrix to connect the Spring Name with ranked mean value.
ranked_spring_matrix<-matrix(ranked_springs_values,ncol=1, byrow=T)
ranked_spring_names<-c("Too Hot Spring","Bluebell Spring","Pearl Spring","Opal Spring","Black Spring","Mystery Spring", "Emerald Spring", "Riverside Spring")
rank<-"Rank Order"
rownames(ranked_spring_matrix)<-ranked_spring_names
colnames(ranked_spring_matrix)<-rank
ranked_spring_matrix
```

```
##                  Rank Order
## Too Hot Spring     39.46667
## Bluebell Spring    35.65000
## Pearl Spring       35.46667
## Opal Spring        34.61667
## Black Spring       32.73333
## Mystery Spring     30.85000
## Emerald Spring     30.20000
## Riverside Spring   29.85000
```



## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences.  
