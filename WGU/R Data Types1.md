```R 
##### Add and delete elements of a list

A numbered element can be added while skipping positions. In the following example the position 3 is left undefined (NULL).

L <‐ list(1,2)
L[4] <‐ 4 # position 3 is NULL
L
## [[1]]
## [1] 1
##
## [[2]]
## [1] 2
##
## [[3]]
## NULL
##
## [[4]]
## [1] 4

  
  

Named elements are always added at the end of the list:

L$pi_value <‐ pi
L
## [[1]]
## [1] 1
##
## [[2]]
## [1] 2
##
## [[3]]
## NULL
##
## [[4]]
## [1] 4
##
## $pi_value
## [1] 3.141593

  
  

Delete an element by assigning NULL to it:

L[1] <‐ NULL
L
## [[1]]
## [1] 2
##
## [[2]]
## NULL
##
## [[3]]
## [1] 4
##
## $pi_value
## [1] 3.141593

  
  

It is also possible to delete an element via the squared brackets. Note that if we address the elements of a list by their number, we need to recalculate the numbers. If we were addressing the elements of the list by name, nothing needs to be changed.

L <‐ L[‐2]
L
## [[1]]
## [1] 2
##
## [[2]]
## [1] 4
##
## $pi_value
## [1] 3.141593

Warning – Deleting elements in lists

When deleting an element in a list, the numbering will change so that it appears that the deleted element was never there. This implies that when accessing elements of the list by number, it is unsafe to delete elements and can lead to unwanted side effects of the code.

##### Convert list to vectors

Vectors can only contain one type of variable, while a list can be of mixed types. It might make sense to convert lists to vectors, for example, because some operations on vectors will be significantly faster.

To do this R, provides the function `unlist()`.

|   |
|---|
|`unlist()`|

  

L <‐ list(c(1:5), c(6:10))
v1 <‐ unlist(L[1])
v2 <‐ unlist(L[2])
v2‐v1
## [1] 5 5 5 5 5

Warning – Silent failing of

Lists are more complex than vectors, instead of failing with a warning and requiring additional options to be set, the `unlist()` function will silentlymake some decisions for you.

# A list of vectors of integers:
L <‐ list(1L,c(‐10L:‐8L))
unlist(L)
## [1]       1      -10    -9     -8
# Note the named real‐valued extra element:
L <‐ list(c(1:2),c(‐10:‐8), "pi_value" = pi)
unlist(L)
##
##     1.000000     2.000000     -10.000000   -9.000000    -8.000000
##     pi_value
##     3.141593

Apart from performance considerations, it might also be necessary to convert parts of a list to a vector, because some functions will expect vectors and will not work on lists.

### Factors

Factors are the objects which hold a series of labels. They store the vector along with the distinct values of the elements in the vector as label. Factors are in many ways similar to the `enum` data type in C, C++ or Java, here they are mainly used to store named constants. The labels are always of the character‐type3 irrespective of data type of the elements in the input vector.

|   |
|---|
|factor|

#### Creating factors

Factors are created using `factor()` the function.

|   |
|---|
|`factor()`|

  

# Create a vector containing all your observations:
feedback <‐ c('Good','Good','Bad','Average','Bad','Good')
# Create a factor object:
factor_feedback <‐ factor(feedback)
# Print the factor object:
print(factor_feedback)
## [1] Good  Good   Bad    Average Bad  Good
## Levels: Average Bad Good

  
  

From the aforementioned example it is clear that the factor‐object "is aware" of all the labels for all observations as well as the different levels (or different labels) that exist. The next code fragment makes clear that some functions – such as `plot()` – will recognize the factor‐object and produce results that make sense for this type of object. The following line of code is enough to produce the output that is shown in Figure [1.11.1](https://learn.zybooks.com/zybook/WGUD276v2/chapter/1/section/11?content_resource_id=93167526).

# Plot the histogram ‐‐ note the default order is alphabetic
plot(factor_feedback)

Figure 1.11.1: The plot‐function will result in a bar‐chart for a factor‐object.

![Bar chart depicts the plot-function will result in a bar-chart for a factor-object.](https://zytools.zybooks.com/zyAuthor/TheBigRBook/1/IMAGES/4e68b6dc-eca4-4cec-af7d-c2897b6fc0c9)

There are a few specific functions for the factor‐object. For example, the function `nlevels()` returns the number of levels in the factor object.

|   |
|---|
|`nlevels()`|

  

# The nlevels function returns the number of levels:
print(nlevels(factor_feedback))
## [1] 3

Digression – The reduced importance of factors

When R was in its infancy, both computing power and memory were not at the level as today and in most cases it made sense to coerce strings to factors. For example, the base‐R functions to load data in a data‐frame (i.e. two dimensional data) will silently convert strings to factors. Today, that is most probably not what you need. Therefore, we recommend to make it a habit to use the functions from the `tidyverse` (see the chapter titled "_Tidy R with the Tidyverse_".

#### Ordering factors

In the example about creating a factor‐object for feedback one will have noticed that the plot function does show the labels in alphabetical order and not in an order that for us – humans – would be logical. It is possible to coerce a certain order in the labels by providing the levels – in the correct order – while creating the factor‐object.

feedback <‐ c('Good','Good','Bad','Average','Bad','Good')
factor_feedback <‐ factor(feedback,
                     levels=c("Bad","Average","Good"))
plot(factor_feedback)

  
  

In Figure [1.11.1](https://learn.zybooks.com/zybook/WGUD276v2/chapter/1/section/11?content_resource_id=93167526) we notice that the order is now as desired (it is the order that we have provided via the attribute `labels` in the function `factor()`.

##### Generate factors with the function `gl()`

Function use for

gl(n, k, length = n*k, labels = seq_len(n), ordered = FALSE)
with

- n: The number of levels
- k: The number of replications (for each level)
- length (optional): An integer giving the length of the result
- labels (optional): A vector with the labels
- ordered: A boolean variable indicating whether the results should be ordered.

|   |
|---|
|`gl()`|

  

gl(3,2,,c("bad","average","good"),TRUE)
## [1] bad   bad    average average good     good
## Levels: bad < average < good

Figure 1.11.2: The factor objects appear now in a logical order.

![Bar chart depicts the factor objects appear now in a logical order.](https://zytools.zybooks.com/zyAuthor/TheBigRBook/1/IMAGES/4b527cf7-e73c-4d56-8e1b-d7509f484261)

Exercise

1.11.3: Question #4.

(a)

Use the dataset mtcars (from the libraryMASS) and explore the distribution of number of gears. Then explore the correlation between gears and transmission.

Exercise

1.11.4: Question #5.

(a)

Then focus on the transmission and create a factor‐object with the words "automatic" and "manual" instead of the numbers 0 and 1.

Use the `?mtcars` to find out the exact definition of the data.

|   |
|---|
|mtcars|

Exercise

1.11.5: Question #6.

(a)

Use the dataset mtcars (from the libraryMASS) and explore the distribution of the horsepower (hp). How would you proceed to make a factoring (e.g. Low, Medium, High) for this attribute? Hint: Use the function `cut()`.

|   |
|---|
|`cut()`|

### Data frames

#### Introduction to data frames

Data frames are the prototype of all two‐dimensional data (also known as "rectangular data"). For statistical analysis this is obviously an important data‐type.

|   |
|---|
|data frame  <br>rectangular data|

  

Data frames are very useful for statistical modelling; they are objects that contain data in a tabular way. Unlike a matrix in data frame each column can contain different types of data. For example, the first column can be factorial, the second logical, and the third numerical. It is a composite data type consisting of a list of vectors of equal length.

Data frames are created using the `data.frame()` function.

|   |
|---|
|`data.frame()`|

  

# Create the data frame.
data_test <‐ data.frame(
  Name = c("Piotr", "Pawel","Paula","Lisa","Laura"),
  Gender = c("Male", "Male","Female", "Female","Female"),
  Score = c(78,88,92,89,84),
  Age = c(42,38,26,30,35)
  )
print(data_test)
##     Name   Gender       Score  Age
## 1   Piotr  Male         78     42
## 2   Pawel  Male         88     38
## 3   Paula  Female       92     26
## 4   Lisa   Female       89     30
## 5   Laura  Female       84     35
# The standard plot function on a data‐frame (figure below)
# with the pairs() function:
plot(data_test)

  
  

|   |
|---|
|`pairs()`|

Figure 1.11.3: The standard plot for a data frame in R shows each column printed in function of each other. This is useful to see correlations or how generally the data is structured.

![Schematic illustration of the standard plot for a data frame in R shows each column printed in function of each other. This is useful to see correlations or how generally the data is structured.](https://zytools.zybooks.com/zyAuthor/TheBigRBook/1/IMAGES/b486f913-6d08-464f-bc68-781fcb6e41ea)

#### Accessing information from a data frame

Most data is rectangular, and in almost any analysis we will encounter data that is structured in a data frame. The following functions can be helpful to extract information from the data frame, investigate its structure and study the content.

|   |
|---|
|`summary()`  <br>`head()`  <br>`tail()`|

  

# Get the structure of the data frame:
str(data_test)
## 'data.frame':   5 obs. of 4 variables:
## $ Name : Factor w/ 5 levels "Laura","Lisa",..: 5 4 3 2 1
## $ Gender: Factor w/ 2 levels "Female","Male": 2 2 1 1 1
## $ Score : num 78 88 92 89 84
## $ Age : num 42 38 26 30 35

  

# Note that the names became factors (see warning below)

# Get the summary of the data frame:
summary(data_test)
##     Name   Gender       Score  Age
## Laura:1    Female:3     Min. :78.0   Min. :26.0
## Lisa :1    Male:2       1st Qu.:84.0       1st Qu.:30.0
## Paula:1          Median :88.0       Median :35.0
## Pawel:1          Mean :86.2   Mean :34.2
## Piotr:1          3rd Qu.:89.0       3rd Qu.:38.0
##                   Max. :92.0   Max. :42.0

# Get the first rows:
head(data_test)
##     Name   Gender       Score  Age
## 1   Piotr  Male         78     42
## 2   Pawel  Male         88     38
## 3   Paula  Female       92     26
## 4   Lisa   Female       89     30
## 5   Laura  Female       84     35

# Get the last rows:
tail(data_test)
##     Name   Gender       Score  Age
## 1   Piotr  Male         78     42
## 2   Pawel  Male         88     38
## 3   Paula  Female       92     26
## 4   Lisa   Female       89     30
## 5   Laura  Female       84     35

# Extract the column 2 and 4 and keep all rows
data_test.1 <‐ data_test[,c(2,4)]
print(data_test.1)
##     Gender       Age
## 1   Male         42
## 2   Male         38
## 3   Female       26
## 4   Female       30
## 5   Female       35

# Extract columns by name and keep only selected rows
data_test[c(2:4),c(2,4)]
##     Gender       Age
## 2   Male         38
## 3   Female       26
## 4   Female       30

Warning – Avoiding conversion to factors

The default behaviour of R is to convert strings to factors when a data.frame is created. Decades ago this was useful for performance reasons. Now, this is usually unwanted behaviour.4 To avoid this put `stringsAsFactors = FALSE` in the `data.frame()` function.

d <‐ data.frame(
  Name = c("Piotr", "Pawel","Paula","Lisa","Laura"),
  Gender = c("Male", "Male","Female", "Female","Female"),
  Score = c(78,88,92,89,84),
  Age = c(42,38,26,30,35),
  stringsAsFactors = FALSE
  )
d$Gender <‐ factor(d$Gender) # manually factorize gender
str(d)
## 'data.frame': 5 obs. of 4 variables:
## $ Name : chr "Piotr" "Pawel" "Paula" "Lisa" …
## $ Gender: Factor w/ 2 levels "Female","Male": 2 2 1 1 1
## $ Score : num 78 88 92 89 84
## $ Age : num 42 38 26 30 35

#### Editing data in a data frame

While one usually reads in large amounts of data and uses an IDE such as RStudio that facilitates the visualization and manual modification of data frames, it is useful to know how this is done when no graphical interface is available. Even when working on a server, all these functions will always be available.

|   |
|---|
|`de()`  <br>`data.entry()`  <br>`edit()`|

  

de(x)  # fails if x is not defined
de(x <‐ c(NA))          # works
x <‐ de(x <‐ c(NA))     # will also save the changes
data.entry(x)           # de is short for data.entry
x <‐ edit(x)            # use the standard editor (vi in *nix)

  
  

Of course, there are also multiple ways to address data directly in R.

# The following lines do the same.
data_test$Score[1] <‐ 80
data_test[3,1] <‐ 80

#### Modifying data frames

##### Add columns to a data‐frame

Typically, the variables are in the columns and adding a column corresponds to adding a new, observed variable. This is done via the function `cbind()`.

|   |
|---|
|`cbind()`|

  

# Expand the data frame, simply define the additional column:
data_test$End_date <‐ as.Date(c("2014-03-01", "2017-02-13",
              "2014-10-10", "2015-05-10","2010-08-25"))
print(data_test)
##     Name   Gender       Score  Age    End_date
## 1   Piotr  Male         80     42     2014-03-01
## 2   Pawel  Male         88     38     2017-02-13
## 3   <NA>   Female       92     26     2014-10-10
## 4   Lisa   Female       89     30     2015-05-10
## 5   Laura  Female       84     35     2010-08-25
# Or use the function cbind() to combine data frames along columns:
Start_date <‐ as.Date(c("2012-03-01", "2013-02-13",
                     "2012-10-10", "2011-05-10","2001-08-25"))
# Use this vector directly:
df <‐ cbind(data_test, Start_date)
print(df)
##     Name   Gender       Score  Age    End_date     Start_date
## 1   Piotr  Male         80     42     2014-03-01   2012-03-01
## 2   Pawel  Male         88     38     2017-02-13   2013-02-13
## 3   <NA>   Female       92     26     2014-10-10   2012-10-10
## 4   Lisa   Female       89     30     2015-05-10   2011-05-10
## 5   Laura  Female       84     35     2010-08-25   2001-08-25
# or first convert to a data frame:
df <‐ data.frame("Start_date" = t(Start_date))
df <‐ cbind(data_test, Start_date)
print(df)
##     Name   Gender       Score  Age    End_date     Start_date
## 1   Piotr  Male         80     42     2014-03-01   2012-03-01
## 2   Pawel  Male         88     38     2017-02-13   2013-02-13
## 3   <NA>   Female       92     26     2014-10-10   2012-10-10
## 4   Lisa   Female       89     30     2015-05-10   2011-05-10
## 5   Laura  Female       84     35     2010-08-25   2001-08-25

##### Adding rows to a data‐frame

Adding rows corresponds to adding observations. This is done via the function `rbind().`

|   |
|---|
|`rbind()`|

  

# To add a row, we need the rbind() function:
data_test.to.add <‐ data.frame(
  Name = c("Ricardo", "Anna"),
  Gender = c("Male", "Female"),
  Score = c(66,80),
  Age = c(70,36),
  End_date = as.Date(c("2016-05-05","2016-07-07"))
  )
data_test.new <‐ rbind(data_test,data_test.to.add)
print(data_test.new)
##     Name        Gender       Score  Age    End_date
## 1   Piotr       Male         80     42     2014-03-01
## 2   Pawel       Male         88     38     2017-02-13
## 3   <NA>        Female       92     26     2014-10-10
## 4   Lisa        Female       89     30     2015-05-10
## 5   Laura       Female       84     35     2010-08-25
## 6   Ricardo     Male         66     70     2016-05-05
## 7   Anna        Female       80     36     2016-07-07

##### Merging data frames

Merging allows to extract the subset of two data‐frames where a given set of columns match.

data_test.1 <‐ data.frame(
  Name = c("Piotr", "Pawel","Paula","Lisa","Laura"),
  Gender = c("Male", "Male","Female", "Female","Female"),
  Score = c(78,88,92,89,84),
  Age = c(42,38,26,30,35)
  )
data_test.2 <‐ data.frame(
  Name = c("Piotr", "Pawel","notPaula","notLisa","Laura"),
  Gender = c("Male", "Male","Female", "Female","Female"),
  Score = c(78,88,92,89,84),
  Age = c(42,38,26,30,135)
  )
data_test.merged <‐ merge(x=data_test.1,y=data_test.2,
                     by.x=c("Name","Age"),by.y=c("Name","Age"))
# Only records that match in name and age are in the merged table:
print(data_test.merged)
##     Name   Age    Gender.x     Score.x      Gender.y     Score.y
## 1   Pawel  38     Male         88           Male         88
## 2   Piotr  42     Male         78           Male         78

  
  

|   |
|---|
|`merge()`|

##### Short‐cuts

R will allow the use of short‐cuts, provided that they are unique. For example, in the data‐frame `data_test` there is a column `Name`. There are no other columns whose name start with the letter "N"; hence. this one letter is enough to address this column.

|   |
|---|
|short-cut|

  

data_test$N
## [1] Piotr Pawel Paula Lisa Laura
## Levels: Laura Lisa Paula Pawel Piotr

Warning – Short‐cuts can be dangerous

Use "short‐cuts" sparingly and only when working interactively (not in functions or code that will be saved and re‐run later). When later another column is added the short‐cut will no longer be unique and behaviour is hard to predict and it is even harder to spot the programming error in a part of your code that previously worked fine.

##### Naming rows and columns

In the preceding code, we have named columns when we created the data‐frame. It is also possible to do that later or to change column names …and it is even possible to name each row individually.

# Get the rownames.
colnames(data_test)
## [1] "Name"      "Gender"     "Score"     "Age"     "End_date"

rownames(data_test)
## [1] "1" "2" "3" "4" "5"

colnames(data_test)[2]
## [1] "Gender"

rownames(data_test)[3]
## [1] "3"

# assign new names
colnames(data_test)[1] <‐ "first_name"
rownames(data_test) <‐ LETTERS[1:nrow(data_test)]
print(data_test)
##     first_name   Gender       Score  Age    End_date
## A   Piotr        Male         80     42     2014-03-01
## B   Pawel        Male         88     38     2017-02-13
## C   <NA>         Female       92     26     2014-10-10
## D   Lisa         Female       89     30     2015-05-10
## E   Laura        Female       84     35     2010-08-25

Exercise

1.11.6: Question #7.

(a)

Create 3 by 3 matrix with the numbers 1 to 9,

(b)

Convert it to a data‐frame,

(c)

Add names for the columns and rows,

(d)

Add a column with the column‐totals,

(e)

Drop the second column.

### Strings or the character‐type

Strings are called the "character‐type" in R. They follow some simple rules:

|   |
|---|
|strings|

- strings must start and end with single or double quotes,
- a string ends when the same quotes are encountered the next time,
- until then it can contain the other type of quotes.

Example: Using strings

a <‐ "Hello"
b <‐ "world"
paste(a, b, sep = ", ")
## [1] "Hello, world"
c <‐ "A 'valid' string"
paste()

Note – Paste

In many cases we do not need anything between strings that are concatenated. We can of course supply an empty string as separator (`sep = "`), but it is also possible to use the custom function `pate0()`:

paste0(12, '%')
## [1] "12%"

|   |
|---|
|`past0()`|

##### Formatting with `format()`

In many cases, it will be useful to format a date or number consistently and neatly in plot and tables. The function `format()` is a great tool to start formatting.

|   |
|---|
|`format()`|

Function use for

format(x, trim = FALSE, digits = NULL, nsmall = 0L,
       justify = c("left", "right", "centre", "none"),
       width = NULL, na.encode = TRUE, scientific = NA,
       big.mark = "", big.interval = 3L,
       small.mark = "", small.interval = 5L,
       decimal.mark = getOption("OutDec"),
       zero.print = NULL, drop0trailing = FALSE, …)

- `x` is the vector input.
- `digits` is the total number of digits displayed.
- `nsmall` is the minimum number of digits to the right of the decimal point.
- `scientific` is set to TRUE to display scientific notation.
- `width` is the minimum width to be displayed by padding blanks in the beginning.
- `justify` is the display of the string to left, right or center.

##### Formatting examples

a<‐format(100000000,big.mark=" ",
              nsmall=3,
              width=20,
              scientific=FALSE,
              justify="r")
print(a)
## [1] "     100 000 000.000"

Further information –

More information about the format‐function can be obtained via `?format` or `help(format)`.

##### Other string functions

- `nchar():` returns the number of characters in a string
    
    |   |
    |---|
    |`nchar()`|
    

- `toupper():` puts the string in uppercase
    
    |   |
    |---|
    |`toupper()`|
    
      
    
- `tolower():` puts the string in lowercase
    
    |   |
    |---|
    |`tolower()`|
    
      
    
- `substring(x,first,last):` returns
    
    a substring from x starting with the "first" and ending with the "last"
    
    |   |
    |---|
    |`substring()`|
    
      
    
- `strsplit(x,split):` split
    
    the elements of a vector into substrings according to matches of a substring "split."
    
    there is also a family of search functions: `grep()`,
    
    |   |
    |---|
    |`strsplit()`|
    
      
    
    |   |
    |---|
    |`grep()`|
    

`grepl()`,

|   |
|---|
|`grepl()`|

  

`regexpr()`,

|   |
|---|
|`regexpr()`|

  

`gregexpr()`,

|   |
|---|
|`gregexpr()`|

  

and `regexec()`

|   |
|---|
|`regexec()`|

  

that supply powerful search and replace capabilities.

`sub()`

|   |
|---|
|`sub()`|

  

will replace the first of all matches and `gsub()`

|   |
|---|
|`gsub()`|

  

will replace all matches.

(*2) This behaviour is caused by the dispatcher‐function implementation of an object‐oriented programming model. To understand how this works and what it means, we refer to another chapter.

(*3) The character type in R is what in most other languages would be called a "string." In other words, that is text that – generally – will not allow much arithmetic.

(*4) See the chapter titled "_Tidy R with the Tidyverse_" and note that tibbles (the data‐frame alternative in the tidyverse) do not coerce text to factors.
```