---
tags:
  - statistics
---

Summen av alle verdier på $x$ - snitt, samme med $y$, delt på $n$

**Covariance** - an unstandardized statistical meaure summarizing the general pattern of association (or the lack thereof) between two continous [[variables]]. 

# covariance between variables $X$ and $Y$
$$
\text{cov}_{XY} = 
\frac
{\sum^n_{i = 1}(X_i - \bar X)(Y_i - \bar Y)}
{n - 1}
$$

Think of individual cases in terms of their values relative to the mean of $X$ $(\bar X)$, and the mean of $Y$ ($\bar Y$): 

- If $X_i$ > $\bar X$ and $Y_i$ > $\bar Y$, that case's contribution to the numerator in the covariance equation will be positive, and if both are less, the cases contribution is also positive. 
- If $X_i$ and $Y_i$ have different signs, its contribution will be negative.

When the covariance between two variables is positive, we find a positive relationship, when it's negative its a negative relationship, and when close to zero, no or little relationship.

In order to get any tell if we can be confident that this relationship is different from what we would see if $X$ and $Y$ were not related in the underlying population, we can use: ![[pearson's R]]
Additionally we can calculate a [[t-statistic]] for a correlation coefficient:
$$t_R = \frac{r\sqrt{n - 2}}{\sqrt{1 - r^2}}$$
$n-2$ are the degrees of freedom.
Using the t-statistic and [[degrees of freedom]], we can look at a table of [[t-table|critical values for t]] 