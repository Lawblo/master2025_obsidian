$$\sum^n_{i = 1}\hat u^2_i$$
Adds together the squared value of each of the residuals for each line.

Formula for bivariate OLS-regression:
$$\hat \beta = \frac
{\sum^n_{i=1}(X_i - \bar X)(Y_i - \bar Y)}
{\sum^n_{i=1}(X_i - \bar X)^2}$$
$\hat \beta$ (the estimated [[coefficient]]) tells us, on average, how many units of change in $Y$ we should expect given a one-unit increase in $X$.
$$\hat \alpha = \bar Y - \hat \beta \bar X$$
Numerator for $\hat \beta$ is the same as numerator for calculating [[covariance]] between $X$ and $Y$.
Denominator for $\hat \beta$ is the sum of squared deviations of the $X_i$ values from $\bar X$.

Thus, for a given covariance between $X$ and $Y$, the more spread out $X$ is, the less steep the estimated slope of the regression line.

The line OLS line goes through the sample mean values of $X$ and $Y$
Calculating $\hat \alpha$, the intercept?:
Start out at the point defined by the mean values, then use the estimated slope, $\hat \beta$, to draw a line. The value of $X$ where $Y$ equals zero is $\hat \alpha$.

Overall fit between $X$ and $Y$: [[goodness-of-fit]]