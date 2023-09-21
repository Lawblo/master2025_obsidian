---
tags:
  - statistics
  - statistical_significance
---
Tests for [[statistical significance]]. Follows the [[t-distribution]].
# Formula for bivariate analysis
ex. duration of government ($Y$) for minority vs majority ($X$).
$$t = \frac{\bar Y_1 - \bar Y_2}{se(\bar Y_1 - \bar Y_2)}$$
$\bar Y_1$ is the mean of the dependent variable for the first value of the independent variable
$\bar Y_2$ is the mean of the dependent variable for the second value of the independent variable
$se$ is the [[standard error]] of the difference between the means

Greater difference between means, and the less dispersed (measured by [[standard deviation]]s) $\Longrightarrow$ greater confidence that $\bar Y_1$ and $\bar Y_2$ are different from eachoter.
## Reading a table of critical values of $t$
Columns are defined by targetet [[p-value]]s, and, to achieve a particular target $p$-value, you need to obtaina particular value of $t$. The rows indicate the number of [[degrees of freedom]]. 

As the number of df goes up, the $t$-statistic we need to obtain a praticular $p$-value goes down.