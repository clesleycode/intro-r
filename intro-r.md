Intro to R Programming
==================

Brought to you by [Lesley Cordero](http://www.columbia.edu/~lc2958).

## Table of Contents

- [0.0 Setup](#00-setup)
	+ [0.1 R and R Studio](#01-r-and-r-studio)
	+ [0.2 Packages](#02-packages)
- [1.0 Data Types and Operators](#10-data-types-and-operators)
	+ [1.1 Math and Numbers](#11-math-and-numbers)
	+ [1.2 Booleans and Equality](#12-booleans-and-equality)
	+ [1.3 Comparisons](#13-comparisons)
	+ [1.4 Strings](#14-strings)
	+ [1.5 Printing](#15-printing)
- [2.0 Control Flow](#20-control-flow)
	+ [2.1 If/Else](#21-if/else)
	+ [2.2 For Loops](#22-for-loops)
	+ [2.3 While Loops](#23-while-loops)
	+ [2.4 Try/Except](#24-try/except)
- [7.0 Final Words](#60-final-words)
	+ [7.1 Resources](#61-resources)
	+ [7.2 More!](#72-more)



## 0.0 Setup 

This guide was written in R 3.2.3.


### 0.1 R and R Studio

Download [R](https://www.r-project.org/) and [R Studio](https://www.rstudio.com/products/rstudio/download/).


### 0.2 Packages

Next, to install the R packages, cd into your workspace, and enter the following, very simple, command into your bash: 

```
R
```

This will prompt a session in R! From here, you can install any needed packages. For the sake of this tutorial, enter the following into your terminal R session:

```
install.packages("")
```

### 0.3 What is R?

R is a powerful language used widely for data analysis and statistical computing. This was possible only because of generous contributions by R users globally. Inclusion of powerful packages in R has made it more and more powerful with time. Packages such as dplyr, tidyr, readr, data.table, SparkR, ggplot2 have made data manipulation, visualization and computation much faster.

### 0.4 Why use R?

- It’s open source
- Availability of instant access to over 7800 packages customized for various computation tasks.
- High performance computing experience 
- One of highly sought skill by analytics and data science companies.


## 1.0 Data Types and Operators

Every programming language needs to store data and a way to work with this data. R, like other languages, breaks these data into types and provides different ways to interact with them. 

Everything you see or create in R is an object. A vector, matrix, data frame, even a variable is an object. R treats it that way. So, R has 5 basic classes of objects, including:

- Character
- Numeric (Real Numbers)
- Integer (Whole Numbers)
- Complex
- Logical (True/False)

These classes have attributes, such as the following:

- names 
- dimension names
- dimensions
- class
- length

Attributes of an object can be accessed using `attributes()` function. 


## 1.1 Vectors

The most basic object in R is known as vector, which contains objects of the same class. You can create an empty vector using `vector()`. 

Let’s try creating vectors of different classes. We can create vector using `c()`:

``` R
a <- c(1.8, 4.5)   #numeric
b <- c(1 + 2i, 3 - 6i) #complex
d <- c(23, 44)   #integer
e <- vector("logical", length = 5)
```


### 1.2 Lists

Lists are present in R, as well as most other programming languages. A list is a data structure that can hold any number of any types of other data structures. For example, if you have vector, a dataframe, and a character object, you can put all of those into one list object. 

#### Initiliazation

To initialize a list to a certain number of components, we use the vector function like this:

``` R
list2 <- vector("list", 3)
```

#### Constructing a List

``` R
vec <- 1:4
df <- data.frame(y = c(1:3), x = c("m", "m", "f"))
char <- "Hello!"
```

Then you can add all three objects to one list using list() function:

``` R
list1 <- list(vec, df, char)
```

You can also turn an object into a list by using the `as.list()` function. Notice how every element of the vector becomes a different component of the list:


#### Manipulating a List
We can put names on the components of a list using the `names()` function, which is useful for extracting components. We could have also named the components when we created the list.

``` R
names(list1) <- c("Numbers", "Some.data", "Letters")
```

#### Extracting Components

The first way in which you can extract an object from the list is by using the [[ ]] operator. 

``` R
list1[[3]]
```

It's also possible to extract components using the component’s name, as shown below:

``` R
list1$Letters
```

#### Subsetting a List

If you want to take a subset of a list, you can use the [ ] operator and c() to choose the components: 

``` R
list1[c(1, 3)]
```

We can also add a new component to the list or replace a component using the $ or [[ ]] operators, such as the following two examples: 

``` R
list1$newthing <- lm(y ~ x, data = df)
```

``` R
list1[[5]] <- "new component"
```

Finally, we can delete a component of a list by setting it equal to NULL:

``` R
list1$Letters <- NULL
```

### Describing Lists

#### Class

The class of the list and the class of one of the components of the list.

``` R
class(list1)
```
and 
```
class(list1[[1]])
```

#### Size 

You can find the size of a list with the `length()` method, like in the following:

``` R
length(list1)
```

#### Converting

Finally, we can convert a list into a matrix, dataframe, or vector in a number of different ways. The first, most basic way is to use unlist(), which just turns the whole list into one long vector:

``` R
unlist(list1)
```

### 1.3 Matrices

When a vector is introduced with row and columns (the dimension attribute), it becomes a matrix. It consist of elements of same class, such as the following:

``` R
my_matrix <- matrix(1:6, nrow=3, ncol=2)
```

### 1.4 DataFrame

DataFrames are used to store tabular data. It's different from matrix where every element must have same class. In a data frame, you can put list of vectors containing different classes. This means that every column of a data frame acts like a list. 

``` R
df <- data.frame(name = c("ash","jane","paul","mark"), score = c(67,56,87,91))
```

## 2.0 Control Flow

What good is a program if we can't make decisions? Luckily, we have several tools at our disposal that allow us to make these decisions, which direct the way our program executes in such a way to make it meaningful.


### 2.1 If/Else

This structure is used to test a condition. Below is the syntax:

``` R
if (condition) {
         ## do something
} 
else {
         ## do something
}
```

### 2.2 For Loops

This structure is used when a loop is to be executed fixed number of times. It is commonly used for iterating over the elements of an object (list, vector). Below is the syntax:

``` R
for (i in range) {
          # do something
}
```

### 2.3 While Loops

This structure begins by testing a condition, and executes only if the condition is found to be true. Once the loop is executed, the condition is tested again. Hence, it’s necessary to alter the condition such that the loop doesn’t go infinity. Below is the syntax:

``` R
while(varable < 17) {
	# do something
}
```

## 5.0 Final Words

### 5.1 Resources



