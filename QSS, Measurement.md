---
title: "ch3_measurement"
author: "Thorkil Schjødt"
date: "2023-09-05"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```


# 3 - Measurement

```{r echo=FALSE}
afghan <- read.csv("../../../data/qss/MEASUREMENT/afghan.csv",
                   stringsAsFactors = TRUE)
```

## 3.1 - Measuring Civilian Victimization during Wartime
### Public opinion survey from southern Afghanistan

```{r echo=FALSE}
summary(afghan$age) #age
```

```{r echo=FALSE}
summary(afghan$educ.years) #educ.years
```

```{r echo=FALSE}
summary(afghan$employed) #employed
```

```{r echo=FALSE}
summary(afghan$income) #income
```

Experienced violence from ISAF (2nd row) and Taliban (2nd column)

```R
prop.table(table(ISAF = afghan$violent.exp.ISAF,
           Taliban = afghan$violent.exp.taliban))
```


## 3.2 - Handling Missing Data in R

Usually coded as `NA`

Print income data for first 10 respondents
```R
head(afghan$income, n = 10)
```

Check whether respondents' income is missing:
```{r}
head(is.na(afghan$income), n = 10)
```

Sixth and tenth are missing

Counting total missing values:
```{r}
sum(is.na(afghan$income))
```

Proportion missing:
```{r}
mean(is.na(afghan$income))
```

`mean` function can take the argument `rm.na = TRUE` to remove missing data.
Other functions, such as `max`, `min`, and `median` also accept this argument.

Some functions, such as the `table` function, ignore missing data, as if these
observations were not a part of the dataset. We can force these functions to
account for missing data, by setting the `exclude` argument to `NULL`.

```{r}
prop.table(table(ISAF = afghan$violent.exp.ISAF,
                 Taliban = afghan$violent.exp.taliban, exclude = NULL))
```

The `na.omit` fucntion removes all observations with at least one missing value 
from a data frame, and returns a new data frame without these observations. 

## 3.3 - Visualizing the Univariate Distribution

### 3.3.1 BAR PLOT

Making bar plots by specifying a certain range for y-axis for ISAF:
```{r}
(ISAF.ptable <- prop.table(table(afghan$violent.exp.ISAF, exclude = NULL)))
barplot(ISAF.ptable,
        names.arg = c("No harm", "Harm", "Nonresponse"),
        main = "Civilian victimization by the ISAF",
        xlab = "Response category",
        ylab = "Proportino of the respondents", ylim = c(0, 0.7))

```

and by the Taliban:
```R
Taliban.ptable <- prop.table(table(Taliban = afghan$violent.exp.taliban,
                                   exclude = NULL))
barplot(Taliban.ptable,
        names.arg = c("No harm", "Harm", "Nonresponse"),
        main = "Civilian victimization by the Taliban",
        xlab = "Response category",
        ylab = "Proportino of the respondents", ylim = c(0, 0.7))
```


Barplot arguments:

- `main`: a character string. Main title.
- `ylab`, `xlab`: character strings. Labeling the axis. Defaults are set if 
unspecified.
- `ylim`, `xlim`: numeric vectors of lenth 2 specifying the interval. Defaults
are set if unspecified.

### 3.3.2 HISTOGRAM

A common method for visualizing the distribution of a *numeric* variable, rather
than a factor variable. 

```{r}
hist(afghan$age, freq = FALSE, ylim = c(0, 0.04), xlab = "Age",
     main = "Distribution of respondent's age")
```

<center>
-------------------------------------------------------
A **histogram** divides the data into bins where the area of each bin represents the proportion of observations that fall within the bin. The height of each bin represents **density**, which is equal to the proportion of observations within each bin divided by the width of the bin. A histofram approximates the distribution of a variable.

---
</center>

You can also choose the bins, instead of letting R set them.
```{r}
# Histogram of education, using "breaks" to choose bins
hist(afghan$educ.years, freq = FALSE,
     breaks = seq(-0.5, 18.5, 1),
     xlab = "Years of education",
     main = "Distribution of respondent's education")

# Adding a text label at (x, y) = (3, 0.5)
text(x = 3, y = 0.5, "median")

# Adding a vertical line representing the median
# `lines` could also be used to place a vertical line:
# lines(x = rep(median(afghan$educ.years), 2), y = c(0, 0.5))

abline(v = median(afghan$educ.years))
```

The `abline` function can add a straight line to an existing plot in three ways:

1. `abline(h=x)` to place a horizontal line at height x
2. `abline(v=x)` to place a vertical line at point x
2. `abline(a=y, b=s)` to place a vertical line with intercept `y` and slope `s`

### 3.3.3 BOX PLOT

### 3.3.4 PRINTING AND SAVING GRAPHSp

## 3.4 - Survey Sampling
Survey sampling is a process where the 

### 3.4.1 THE ROLE OF RANDOMIZATION


