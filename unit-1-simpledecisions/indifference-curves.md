(content:references:indifference-curves-and-trades)=
# Marginal Utility, Indifference and Trades


```{topic} Outline
In this lecture, we will introduce the concept of indifference curves and marginal rate of substitution.

* [Indifference curves](content:references:indifference-curves) are combinations of choices that provide a decision-making agent with the same level of utility. Thus, an indiffrence curve is a `isohappiness` curve in the space of choices. 

* [Marginal rate of substitution](content:references:marginal-rate-of-sub) is the rate at which a consumer is willing to trade one good for another. The marginal rate of substitution is derived from the local expansion of the utility function around a starting point $x^{\star}\in{X}$, where $X$ is the set of all possible objects.

```

---

## Introduction
The rational choice theory posits that individuals make choices to maximize their utility. To determine how individuals make choices, we must understand how they value different options. We previously introduced utility functions, which assign a numerical value, called `utility`, to each possible choice or outcome based on how much the individual values it. Additionally, we introduced the concept of [marginal utility](content:references:marginal-utility), which is the change in utility resulting from a change in the consumption of a good or service or the change in a feature variable associated with a good or service.

In this lecture, we will introduce the concept of indifference curves, which are combinations of choices that provide a decision-making agent with the same level of utility. Thus, an indiffrence curve is a `isohappiness` curve in the space of choices. Indifference curves are a key tool in consumer theory, and are used to model the preferences of consumers. 

```{admonition} Key Idea: Indifference
An indifference curve is a curve in the space of choices that represents a set of choices that provide the same level of utility to the decision-maker, i.e., $dU=0$. Decision-makers are indifferent between any choices that lie on the same indifference curve.
```

(content:references:indifference-curves)=
## Indifference curves
If a decision-maker is indifferent between any two choices that provide the same level of utility, then we can plot the set of all choices that provide the same level of utility. This set of choices is called an indifference curve. Let the decision maker's utility function be $U:X\rightarrow\mathbb{R}$, where $X$ is the set of all possible objects. Then, the indifference curve is given by:

```{math}
:label: eqn-indifference-curve
U(x^{\star}_{1},\dots,x^{\star}_{m}) - U^{\star} = 0
```

where $U^{\star}$ is the level of utility provided by the set of choices on the indifference curve, and $x^{\star}_{1},\dots,x^{\star}_{m}$ are the choices that provide the level of utility $U_{\star}$. 

```{admonition} Key Idea: Indifference curves
Indifference curves are combinations of choices that provide a decision-making agent with the same level of utility. Thus, an indiffrence curve is a `isohappiness` curve in the space of choices. 
```

The challenge that we have to solve for the set of choices that provide the same level of utility, which is difficult because the utility function is not necessarily linear. Thus, we cannot simply solve for the set of choices that provide the same level of utility by setting the utility function equal to a constant. 

Instead, we must use the local expansion of the utility function around a starting point $x^{\star}\in{X}$, where $X$ is the set of all possible objects. For some utility function $U:X\rightarrow\mathbb{R}$, the local expansion of the utility function around $x^{\star}$ is given by:

We can use marginal utility to approximate how utility changes when consumption or features of a good or service are changed around a starting point $x^{\star}\in{X}$, where $X$ is the set of all possible objects. The total change in utility is given by:

```{math}
dU = \sum_{i\in{1\dots{n}}}\bar{U}_{x_{i}}\cdot{dx_{i}}
```

where $dU\approx\left(U - U_{\star}\right)$ denotes the change in utility, $\bar{U}_{x_{i}}$ denotes the marginal utility of $x_{i}$ evaluated at the starting point, and $dx_{i}\approx(x_{i}-x_{i,\star})$ is the change in $x_{i}$. In the local area around $x^{\star}$, 

(content:references:marginal-rate-of-sub)=
## Marginal Rate of Substitution
The marginal rate of substitution describes the rate at which a consumer is willing to trade one good (or feature) for another. We can derive the marginal rate of substitution from the local expansion of the utility function around a starting point $x^{\star}\in{X}$, where $X$ is the set of all possible objects. For some utility function $U:X\rightarrow\mathbb{R}$, the marginal rate of substitution between any two goods (or features) $x_{i}$ and $x_{j}$ along the indifference curve, i.e., a curve where `dU = 0`, is given by:

```{math}
\bar{U}_{x_{i}}\,dx_{i} = -\bar{U}_{x_{j}}\,dx_{j}\qquad{\forall{i\neq{j}}}
```

or equivalently:

```{math}
\frac{dx_{i}}{dx_{j}} = -\frac{\bar{U}_{x_{j}}}{\bar{U}_{x_{i}}}\qquad{\forall{i\neq{j}}}
```

---

## Summary
Fill me in.