
R is a modern language with a rather short history. In 1992, the R‐project was started by Ross Ihaka and Robert Gentleman at the University of Auckland, New Zealand. The first version was available in 1995, and the first stable version was available in 2000.

Now, the R Development Core Team (of which Chambers is a member) develops R further and maintains the code. Microsoft has embraced the project for a few years and provides MRAN (Microsoft R Application Network). This package is also free, and an open source software (FOSS) has some advantages over standard R, such as enhanced performance (Ex. multi‐thread support, the checkpoint package that makes results more reproducible).

*Important function used throughout*
- c() - Generic function that combines arguments to form a vector. All args are coerced to a common type.
	- recursive = TRUE, the function recursively descends through lists to combine elements
	- use.names - logical indicating if names should be preserved
# Variables

Can contain letters as well as *_* and "."
They must start with a letter (can be preceded by a dot)

### Assignment

Can be made left or right  -> OR <-
R allows left assignments with the = sign .... x.3 = 3.14
The = operator must be used when assigning values to named inputs for functions
 - v1 <- c(1,2,3,NA)
 - mean(v1, na.rm = TRUE)

ls() lists all variables (hidden variables start with a dot)
ls(all.names=TRUE) - shows all
rm() removes a variable
rm(list = ls()) removes all variables

A variable whose name starts with a dot (e.g. `.x`) is in all aspects the same as a variable that starts with a letter. The only difference is that the first will be hidden with the standard arguments of the function `ls()`.

### Types

R assigns classes automatically
Can use class() to determine class of variable

- Boolean - TRUE FALSE
- Integer can use L for long integer
- Decimal numbers are referred to as 'numeric'
- Complex numbers use "i" - 3.2i
- Strings are called 'character'
- Date - d <‐ as.Date(c("1852-05-12", "1914-11-5", "2015-05-01"))
	- d_recent <‐ subset(d, d > as.Date("2005-01-01"))

#### Vectors 
Vectors are lists of objects that are all of the same type. They can be the result of a calculation or be declared with the function c()
```R
v <‐ c(1:5)                      # Create v as a vector of the numbers one to 5
v[2]                             # Access via iindex
v[c(TRUE,TRUE,FALSE,FALSE,TRUE)] # Access via TRUE/FALSE

v <- c ("pear" = "green", "banana" = "yellow", "coconut" = "brown") 
v["banana"]                      # Access via names

v[c(-2, -3)]                     # Leave out certain elements
```

The standard behaviour for vector arithmetic in R is element per element
##### Vector Recycling
Vector recycling refers to the fact that in case an operation is requested with one too short vector, that this vector will be concatenated with itself till it has the required length.
```R
# Define a short and long vector:
v1 <‐ c(1, 2, 3, 4, 5)
v2 <‐ c(1, 2)

# Note that R 'recycles' v2 to match the length of v1:
v1 + v2

## Warning in v1 + v2: longer object length is not a multiple of shorter object length
## [1] 2 4 4 6 6
```

##### Reordering and sorting
- sort()
```R
v1 <- c(1, -4, 2, 0, pi)
sort(v1)
## [1] -4.000000   0.000000     1.000000     2.000000     3.141593

To make sorting meaningful, all variables are coerced to # the most complex type:
v1 <‐ c(1:3, 2 + 2i)
sort(v1)
## [1] 1+0i 2+0i 2+2i 3+0i

# Sorting is per increasing numerical or alphabetical order:
v3 <‐ c('January", 'February", 'March", 'April")
sort(v3)
## [1] 'April"     'February"   'January"    'March"
# Sort order can be reversed:
sort(v3, decreasing = TRUE)
## [1] 'March"     'January"    'February"   'April"
```

### Matrices

A matrix is a two dimensional data set where all elements are of the same type
```R
# Create a matrix.
M = matrix( c(1:6), nrow = 2, ncol = 3, byrow = TRUE)
print(M)
##        [,1]   [,2]   [,3]
## [1,]      1      2      3
## [2,]      4      5      6

M = matrix( c(1:6), nrow = 2, ncol = 3, byrow = FALSE)
print(M)
##        [,1]   [,2]   [,3]
## [1,]      1      3      5
## [2,]      2      4      6
```

```R
  

# Unit vector:
matrix (1, 2, 1)
##        [,1]
## [1,]      1
## [2,]      1

# Zero matrix or vector:
matrix (0, 2, 2)
##        [,1]   [,2]
## [1,]      0      0
## [2,]      0      0

# Recycling also works for shorter vectors:
matrix (1:2, 4, 4)
##        [,1]   [,2]   [,3]   [,4]
## [1,]      1      1      1      1
## [2,]      2      2      2      2
## [3,]      1      1      1      1
## [4,]      2      2      2      2
# Fortunately, R expects that the vector fits exactly n times in the matrix:
matrix (1:3, 4, 4)
## Warning in matrix(1:3, 4, 4): data length [3] is not a sub-multiple or multiple of the number of rows [4]
##        [,1]   [,2]   [,3]   [,4]
## [1,]      1      2      3      1
## [2,]      2      3      1      2
## [3,]      3      1      2      3
## [4,]      1      2      3      1

# So, the previous was bound to fail.
```

##### Naming rows and columns

While in general naming rows and/or columns is more relevant for datasets than matrices it is possible to work with matrices to store data if it only contains one type of variable.

```R
row_names = c('row1", 'row2", 'row3", 'row4")
col_names = c('col1", 'col2", 'col3")
M <‐ matrix(c(10:21), nrow = 4, byrow = TRUE,
              dimnames = list(row_names, col_names))

print(M)
##         col1   col2   col3
## row1      10     11     12
## row2      13     14     15
## row3      16     17     18
## row4      19     20     21
```

Once the matrix exists, the columns and rows can be renamed with the functions
 - colnames()
 - rownames()

```R 
colnames(M) <‐ c('C1', 'C2', 'C3')
rownames(M) <‐ c('R1', 'R2', 'R3', 'R4')
```

##### Access subsets of a matrix
```R
M <‐ matrix(c(10:21), nrow = 4, byrow = TRUE)
M
##          [,1]   [,2]   [,3]
## [1,]      10     11     12
## [2,]      13     14     15
## [3,]      16     17     18
## [4,]      19     20     21

# Access one element:
M[1,2]
## [1] 11

# The second row:
M[2,]
## [1] 13 14 15

# The second column:
M[,2]
## [1] 11 14 17 20

# Row 1 and 3 only:
M[c(1, 3),]
##          [,1]   [,2]   [,3]
## [1,]      10     11     12
## [2,]      16     17     18

# Row 2 to 3 with column 3 to 1
M[2:3, 3:1]
##         [,1]   [,2]   [,3]
## [1,]      15     14     13
## [2,]      18     17     16
```

```R
# Example of the dot‐product:
a <‐ c(1:3)
a %*% a
##     [,1]
## [1,]      14

a %*% t(a)
##        [,1]   [,2]   [,3]
## [1,]      1      2      3
## [2,]      2      4      6
## [3,]      3      6      9

t(a) %*% a
##         [,1]
## [1,]      14
# Define A:
A <‐ matrix(0:8, nrow = 3, byrow = TRUE)

# Test products:
A %*% a
##         [,1]
## [1,]      8
## [2,]      26
## [3,]      44

A %*% t(a) # this is bound to fail!

## Error in A %*% t(a): non‐conformable arguments
A %*% A
##         [,1]   [,2]   [,3]
## [1,]      15     18     21
## [2,]      42     54     66
## [3,]      69     90     111

  

There are also other operations possible on matrices. For example the quotient works as follows:

A %/% A
##         [,1]   [,2]   [,3]
## [1,]      NA     1      1
## [2,]      1      1      1
## [3,]      1      1      1
```

#todo #research How dot products work?

- t() - Transposes a matrix
- diag() - Diagonal of a matrix
- det() - Calculates the determinate  #todo #research What is a determinate?
- solve() - Solves the equation A %*\% x = b BUT

```R 
M <‐ matrix(c(1,1,4,1,2,3,3,2,1), 3, 3)
M
##         [,1]   [,2]   [,3]
## [1,]      1      1      3
## [2,]      1      2      2
## [3,]      4      3      1

# The diagonal of M:
diag(M)
## [1] 1 2 1

# Inverse:
solve(M)
##             [,1]       [,2]         [,3]
## [1,]      0.3333333    -0.66666667  0.33333333
## [2,]      -0.5833333   0.91666667   -0.08333333
## [3,]      0.4166667    -0.08333333  -0.08333333

# Determinant:
det(M)
## [1] -12

# The QR composition:
QR_M <‐ qr(M)
QR_M$rank
## [1] 3

# Number of rows and columns:
nrow(M)
## [1] 3

ncol(M)
## [1] 3

# Sums of rows and columns:
colSums(M)
## [1] 6 6 6

rowSums(M)
## [1] 5 5 8

# Means of rows, columns, and matrix:
colMeans(M)
## [1] 2 2 2

rowMeans(M)
## [1] 1.666667 1.666667 2.666667

mean(M)
## [1] 2

# Horizontal and vertical concatenation:
rbind(M, M)
##         [,1]   [,2]   [,3]
## [1,]      1      1      3
## [2,]      1      2      2
## [3,]      4      3      1
## [4,]      1      1      3
## [5,]      1      2      2
## [6,]      4      3      1
cbind(M, M)
##         [,1]   [,2]   [,3]   [,4]   [,5]   [,6]
## [1,]      1      1      3      1      1      3
## [2,]      1      2      2      1      2      2
## [3,]      4      3      1      4      3      1
```

### Arrays

Arrays can have any number of dimensions (unlike a matrix) but they still have the same requirement that all elements are of the same data-type

Arrays can be create with array()
array takes a 'dim' attribute which defines the number of dimensions

```R
a <- array(c('A','B'), dim = c (3,3,2))

# Creates an array with two elements, which are both 3x3 matrices

# Acces one element
a[2,2,2]

# Access ones layer
a[,,2]
```

#### Naming Elements in array
```R 
# Create two vectors
v1 <- c(1, 1)
v2 <- c(10:13)
col.names <- c('col1", 'col2",'col3")
row.name <- c('R1", 'R2")
matrix.names <- c('Matrix1", 'Matrix2")
```

#### Applying functions over arrays

apply(X, MARGIN, FUN, ....) with: 

1. X: an array, including a matrix
2. MARGIN: a vector giving the subscripts which the function will be applied over. E.g. for a matrix '1' indicates rows, '2' indicates columns, c(1,.2) indicates rows and columns. Where 'X' has named dimnames, it can be a character vector selected dimension names. 
3. FUN: the function to be applied.

```R
x <- cbind(x1 = 3, x2 = c(4:1, 2:5))
dimmanes(x)[[1]] <- letters[1:8]
apply(x, 2, mean, trim = .2)
```

### Lists
```R
myList <‐ list("Approximation", pi, 3.14, c)
print(myList)
```

##### Naming elements of lists
```R
# Create the list:
L <‐ list("Approximation", pi, 3.14, c)
# Assign names to elements:
names(L) <‐ c("description", "exact", "approx","function")
print(L)
## $description
## [1] "Approximation"
##
## $exact
## [1] 3.141593
##
## $approx
## [1] 3.14
##
## $`function`
## function (&amp;hellip;) .Primitive("c")

# Addressing elements of the named list:
print(paste("The difference is", L$exact ‐ L$approx))
## [1] "The difference is 0.00159265358979299"

print(L[3])
## $approx
## [1] 3.14

print(L$approx)
## [1] 3.14

# However, "function" was a reserved word, so we need to use
# back‐ticks in order to address the element:
a <‐ L$`function`(2,3,pi,5) # to access the function c(…)
print(a)
## [1] 2.000000 3.000000 3.141593 5.000000
```

##### Double Square Brackets

The double square brackets will inform R that we want one element returned as the most elementary class and is limited to returning one position. The simple square brackets will return a list and can be given a range.

```R
# The first object of L2 as a list:
L2[1]
## [[1]]
## [1] 1 2 3

class(L[2])
## [1] "list"

# The first element of L2 is a numeric vector:
L2[[1]]
## [1] 1 2 3

class(L2[[2]])
## [1] "integer"
```

