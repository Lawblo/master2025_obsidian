---
tags:
  - statistics
  - metode
---
$P$ for probability. "Closest thing to a bottom line is statistics"
# Definition:
>The probability that we would see the relationship that we are finding because of random chance.
>Ranges from 0 to 1.

The probability that we would see the observed relationship between the two variables in our sample data if there were truly no relationship between them in the unobserved population.

- Lower number $\Longrightarrow$ greater confidence of systematic relationship 
- More data $\Longrightarrow$ lower p-value

Larger sample size increase our confidence that the observed relationship in sample accurately represents the underlying population.

$\uparrow$ [[t-test|t-value]] $\Longrightarrow$ $\downarrow$ p-value

A relationship lower than 0.1(\*), 0.05(\*\*), or 0,01 (\*\*\*) is generally required for [[statistical significance]].
# Limitations
- Logic is not reversible $\rightarrow$ *p* = 0.001 does **not** mean that there is a 0.999 chance that something systematic is going on
- Does not speak on causality
- Doesn't say anything about the strength of the relationship
- Do not directly reflect the quality of the [[measurement]] procedure for our [[variables]].

# Assumptions
P-values are always based on the assumptions of a random sample from the underlying population.
$$p_i = P \forall i$$
The probability of an individual case from our population aending up in our sample, $p_i$, is assumed to equal the same value, $P$, for all of the individual cases $i$. 

This standard is almost never met. The further from a truly random sample, the less confidence we should have in the $p$-value.

