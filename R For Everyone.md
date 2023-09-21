#R #lander #sampol305 #metode #statistics 
# Assigning Variables
#variables

Variable names can contain any combination of alphanumberic characters, as well as . and \_, but can't start with the special characters.

Variable names are case sensitive.

Assign variables with `=`, `->`, `<-`, or the `assign`function: 

```R
x <- 2
4 -> z
y = 3
a <- b <- 7
assign("j", 4)
```

`<-` is preferred in the R community.

# Removing Variables

Remove a variable with the `remove` function, or its shortcut `rm`.

	rm(j)

This frees up memory in most cases, but it may be neccesary to use the `gc` function, garbage collections, which releases unused memory to the OS. 

# Data Types
#data-types

The four most important data types are: 
- `numeric`
- `character` (string)
- `Date`/`POSIXct` (time based)
- `logical` (TRUE/FALSE), boolean

use the `class` function to check the type of a variable.

## Numeric Data

The #numeric data type handles integers and decimals, both positive and negative. 

Check if a varaible is numeric with the `is.numeric` function. 

Division by 0 results in `inf`

### Integer

The #integer type also exists, but i less used. Assiging an integer to a variable is done by appending `L` to the value.

Check if a value is an integer with `is.integer`
Integers will also pass the `is.numeric` test. 

Dividing two integers results in a numeric

## Character Data

R has two primary ways of handling character data: #character, and #factor

`x <- "data"` will assign `"data"` to `x`
`y <- factor("data")` will assign `data` without quotation marks to `y`, as well as the `levels` of `y`

Characters are case sensitive. 

Use the `nchar` function to find the length of a string. This does not work for `factor` data

## Dates

R has several different types of dates. The most useful are #Date and #POSIXct. `Date` stores just the date, while `POSIXct` stores both time and date. Both are represented as the number of days (`Date`) or seconds (`POSIXct`) since 01.01.1970.

```R
date1 <- as.Date("2012-06-28")
date2 <- as.POSIXct("2012-06-28 17:42")
```

Easier handling of data and time can be accomplished using the `lubridate` and `chron` packages.

## Logical

#logical is a way of representing data that can be either `TRUE` or `FALSE`. `TRUE` is the same as `1` and `FALSE` is the same as `0`

R provides `T` and `F` as shortcuts for `TRUE` and `FALSE`, but it is best practice not to use these, as they are variables and can thus be overwritten.

Check if a varaible is `logical` with the `is.logical` function. 

`Logical` data can result from comparing two numbers, or characters.

|Symbols|Test|
|:-:|:-:|
|\==|Equality|
|!=|Inequality|
|<|Less than|
|<=|Less or equal than|
|>|Greater than|
|>=|Greater or equal than|


## Vectors

A #vector is a collection of elements, all of the same type.

```R
x <- c(1, 2, 3, 4, 5)
y <- c("R", "STATA", "Excel", "SAS")
```

R is a vectorized language. This means that operations are applied to each element of the `vector` automatically. 

Vectors are 1-dimensional.

### Vector Operations

```R
x <- c(1, 2, 3, 4, 5)
x * 3
>>[1] 3, 6, 9, 12, 15

x + 2
>>[1] 3, 4, 5, 6, 7
```

These operations would not change the `x` variable, only display the contained data with the applied operation.

`:` is a shortcut to create a `vector` with ranges of numbers. This is inclusive. 

```R
1:10
>>[1] 1 2 3 4 5 6 7 8 9 10
10:1
>>[1] 10 9 8 7 6 5 4 3 2 1
-2:3
>>[1] -2 -1 0 1 2 3
```

Vectors can be combined.

```R
x <- 1:10
y <- -5:4
x + y
>>[1] -4 -2 0 2 4 6 8 10 12 14
x - y
>>[1] 6 6 6 6 6 6 6 6 6 6
```

Check the length of a `vector` with the `length` function.

If the vectors are of different lengths, the shorter one gets recycles and restarts from the beginning. If the longer on is not a multiple of the longer one, a warning is shown, however, the code is still ran.

Comparisons also works on a `vector`.

To test whether all elements are `TRUE`, use the `all` function. The `any` function checks if any of the elements are `TRUE`.

`nchar` also works on each element of the vector.

Access an individual element of a `vector` using bracket notation.

| | |
|---|---|
|First element|`x[1]`|
|First two|`x[1:2]`|
|Nonconsecutive elements|`x[c(1, 4)]`| 

It is possible to give names to a `vector` either during creation or later. 

```R
c(One="a", Two="y", Last="r")
>>One  Two Last 
>>"a"  "y"  "r" 

w <- 1:3
names(w) <- c("a", "b", "c")
w
>>abc
>>123
```


### Factor Vectors

```R
q <- c("Hockey", "Football", "Baseball", "Curling", "Rugby", "Lacrosse",
       "Basketball", "Tennis", "Cricket", "Soccer")
q2 <- c(q, "Hockey", "Lacrosse", "Hockey", "Water Polo", "Hockey", "Lacrosse")

q2Factor <- as.factor(q2)
q2Factor

>>[1] Hockey  Football  Baseball  Curling  Rugby  Lacrosse  Basketball
+     Tennis  Cricket  Soccer
>>[11] Hockey  Lacrosse  Hockey  Water Polo  Hockey  Lacrosse
>>Levels: Baseball  Basketball  Cricket  Curling  Football  Hockey
+         Lacrosse  Rugby  Soccer  Tennis  Water Polo
```

The `levels` of a `factor` are the unique values of that `factor` variable. R is giving each unique value of a `factor` a unique `integer`, tying it back to the `character` representation. #hmm 

In ordinary `factors`, the `levels` does not matter, and one `level` is no different from another.
It is possible to assign an explicit order to a factor by setting the `ordered` argument to `TRUE`. 

```R
factor(x=c("High School", "College", "Masters", "Doctorate"),
	   levels=C("High School", "College", "Masters", "Doctorate"),
	   ordered=TRUE)
```

`Factors` can reduce the size of the variable because they're only storing unique values, but can make it more difficult to work with.


## Functions

The `?` symbol can be used befor ethe function to get the function #documentation. To get help on binary operations use the operators in backticks with the `?` prefix. 

Searching for a function if you only remember part of the name can be done with `apropos`, followed by the part of the function you remember. 

## Missing Data

R has two types of missing data, `NA` and `NULL`.

### NA

#NA can exist within a vector.

### NULL

#NULL is the absence of anything.

`NULL` is automatic and can't exist within a vector, where it would simply disappear. It can be the returned value of a function, or it can be a function argument. 

## Pipes

Requires the `magrittr` package. Pipes takes a value or object on the left side, and inserts it into the first argument of the function on the right side. With only the piped argument used, there is no need for parentheseses, but if the are more, then they're required.

```R
x <- 1:10
x %>% mean
> 5.5
```

Pipes can be used to chain together a series of function calls.

# CH2, Advanced Data Structures

R has a host of data structures. The most common are: 
- `data.frame`
- `matrix`
- `list`
- `array`

## data.frames

