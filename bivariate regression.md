---
tags:
  - statistics
  - overview
---
Basic idea: Fitting the "best" line through a scatter plit of data.
# terms
- $\alpha$ = $y$-**inctercept**, $Y$ value when $X$ = 0
- $\beta$ = slope parameter, **[[coefficient]]**
- $Y$ = **dependent** variable
- $X$ = **independent** variable
- $u_i$ = the stochastic or "random" component of dependent variable. "Noise". **[[residuals]]**.
- $\sigma^2$ = **variance**
- $\sigma$ = population [[standard deviation]]

# population regression model
$$Y_i = \alpha + \beta X_i + u_i$$
# sample regression model
$$Y_i = \hat \alpha + \hat \beta X_i + \hat u_i$$
The 'hat' (^) signifies parameter estimates. Best guesses of $\alpha$ (interecept), $\beta$ (coefficient).
$$\hat \beta = $$

## fitting the best line
We want our residual values, $\hat u_i$, to be as small as possible. The way that statisticians tend to prefer is [[ordinary least-squares regression, OLS]] regression.

Measures of the overall fit between a regression model and the dependent variable are called [[goodness-of-fit]] measures.

## uncertainty about individual components of the model
One estimate that factors into the calculations of our uncertainy about each of the population parameters is the estimated [[variance]], $\hat \sigma$ of the population stochastic component, $u_i$. This unseen [[variance]], $\sigma^2$, is estimated from the [[residuals]] ($\hat u_i$) after the parameters for the sample regression model have been estimated by the following formula: 
$$\hat \sigma^2 = \frac{\sum^n_{i = 1}\hat u^2_i}{n-2}$$
Once $\sigma^2$ has been estimated, the variance and standard error for $\hat \beta$ (slope parameter estimate) are then estimated from the following formulae:
$$\text {var}(\hat \beta) = \frac{\hat \sigma ^2}{\sum^n_{i=1}(X_i - \bar X)^2}$$
$$\text{se}(\hat \beta) = \sqrt{\text{var}(\hat \beta)} = \frac{\hat \sigma}{\sum^n_{i=1}(X_i - \bar X)^2}$$

In the numerators, we find $\hat \sigma$ values. So the larger these values are, the larger will be the variance and standard error of the slope parameter estimate. -> The farther the points representing our data are from the regression line, the less confidence we will have in the value of the slope.

In the denominators, we find $\sum^n_{i=1}(X_i - \bar X)^2$, which is a measure fo the variation of the $X_i$ values around $\bar X$. 

The greater this variation, the smaller will be the variance and standard error of the slope parameter estimate -> **The more variation we have in $X$, the more precisely we will be able to estimate the relationship between $X$ and $Y$**.

The variance and standard errors for the intercept parameter estimate ($\hat \alpha$) are then estimated from the following formulae:
$$\text{var}(\hat \alpha) = \frac{\hat \sigma^2 \sum^n_{i=1}X^2_i}{n\sum^n_{i=1}(X_i-\bar X)^2}$$
$$\text{se}(\hat \alpha) = \sqrt{\text{var}(\hat \alpha)}$$
The larger $\hat u_i$ (estimated residuals) are, the larger will be the [[variance]] ($\sigma^2$) and standard error of $\hat \alpha$ (intercept parameter estimates); and the larger the variation of the $X_i$ values around their mean, the smaller will be the variance and standard error of the intercept parameter estimate.

## [[confidence interval]] about parameter estimates
![[confidence interval]]

The traditional appriach to hypothesis testing with OLS regression is that we specify a [[null hypothesis]] and an [[alternative hypothesis]].
We can test hypotheses about both the slope $\beta$ or the intercept $\alpha$. The hypothesis we usually test is that $\beta$ is equal to zero, which would usually mean that a change in $X$ doesnt change what we would expect $Y$ to be.

# two-tailed hypothesis tests
## testing the coefficient

![[null hypothesis]]
![[alternative hypothesis]]
Testing which hypothesis is supported, is done by calculating a ![[t-ratio]]
Again, check the $t$ value for $n$ observations with $k$ degrees of freedom, and check the result against the [[t-table]]. If the [[p-value]] is lower than 0.05, then we have a significant result, which means that it is inlikely that that $H_0$ is the case, which increases the our confidence of $H_1$.
## testing the y-intercenpt, $\alpha$
Same logic. 
$$t_{n-k} = \frac{\hat \alpha - \alpha^*}{\text{se}(\hat \alpha)}$$
$H_0: \alpha = 0$, $H_1: \alpha \ne 0$. This result can be quite high. Would tell us that its less likely that $\alpha$ = 0.

# assumptions
**When we calculate these statistics, we're making a lot of assumptions! Se Kellsted & Whitten, 9.5.**
# forelesning
- Kan **teste** forutsetninger.
- Ulike typer variabler
- ulike typer data
- robuste resultater
- Mange og ulike modellspesifikasjoner.

## Svakheter
- Uobservert heterogenitet
	- Må aktivt finne kontroller. Mange kan skape store skjevheter
- Kontrafaktiske resultater
- Modell-avhengighet
	- Litt for lett å manipulere
	- Kan tilpasse analyse for ønsket resultat
		- Kan velge kontrollvariabler
		- linær vs ikke-linær
		- samspillseffekt
		- ulike nivåer
- Diagnose

## En linær funksjon:
$$Y = a + bX$$
$Y$= avhengig
$X$ = uavhengig
$a$ = konstantledd ($Y$ når $X = 0$)
$b$ = regresjonskoeffisient (gjennomsittlig endring i Y for en enhets økning i x)

## Restleddet
$$Y = { \alpha + \beta X} + {\varepsilon}$$
## Residualer 
$$\hat{e} = Y - (\hat{a} + b\hat{X})$$

$$\hat{e} = Y - \hat{Y}$$
residualene = faktiske - predikerte verdier

Residualenee kommer fra utvalget; de er estimater av det ukjente restleddet

# OLS
Velger a og b slik at $\sum{e^2}$ blir minst mulig.

$$ b = \frac{\sum{(Xi - \bar{X})(Yi - \bar{Y})}}{\sum(Xi - \bar{X})^2}$$

$$a = \bar{Y} - b\bar{X}$$
Regresjonslinjen vil alltid passere gjennom gjennomsnittene til X og Y
Gjenommsnittet til residualene = 0
Residualene vil ikke være korrelert med $X \text{ og } \hat{Y}$ 

# Forklart varians: $R^2$
Sier noe om hvor mye av variasjonen i Y som kan forklares av variasjonen i X. Mellom 0 og 1.

Total varian = Forklart varians + uforklart varians

## Svakheter ved $R^2$
- Sensitiv til type data
	- Høyere for aggregert data
	- Høyere for tidsseriedata
	- Ofte lavere for differensierte variabler
- Påvirket av variasjonen i X (jo mindre variasjon, desto lavere $R^2$) og utelatte X
- Påvirket av målefeil (jo større feil, desto lavere $R^2$)

# Standardfeilen til regresjon
$$\hat{\sigma} = \sqrt{
\frac
{\sum{e^2_i}}
{N - 2}
}$$
Jo mindre standardfeil, desto bedre modell

# Standardfeilen til koeffisienten
"Hvis koeffissienten er dobbelt så stor som standardfeilen er den signifikant". $\rightarrow$ t-verdi
$$
seb = \sqrt{
\frac
{\frac
{\sum{(Yi - \hat{Y})}}
{N - 2}
}
{\sum(Xi - \bar{X})^2}
}
$$
1. $\sum{(Yi - \hat{Y})^2} \uparrow \Longrightarrow se\uparrow$
2. $(N - 2)\uparrow \Longrightarrow se\downarrow$
3. $\sum(Xi - \bar{X})\uparrow \Longrightarrow se\downarrow$

lav sd -> høy t -> lav p

# T-verdi når $H_0: \beta = 0$
# Dummyvariabler
Hvis avhengig, må bruke logistisk regresjon. 

|                      | Bivariat regresjon | X-var I | X-var II |
| -------------------- | ------------------ | ------- | -------- |
| Panelregresjon       |$Y_{it} = \alpha+\beta X_{it}+\varepsilon_{it}$|$X_it$ (tidsvarierende)|$X_i$(tidskonstant)|
| Tverrsnittsregresjon |$Y_i = \alpha + \beta X_i + \varepsilon_i$  |$X_i$                  |               |
| Tidsserieregresjon   |$Y_i = \alpha+\beta X_i+\varepsilon_i$  |$X_t$                  |               |
| Flernivåanalyse      |$Y_{ij}=\alpha+\beta X_{ij}+\varepsilon_{ij}$ |$X_{ij}$(nivå 1)         |$X_{j}$(nivå 2)     |
