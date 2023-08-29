(content:references:indifference-curves-and-trades)=
# Marginal Utility, Indifference and Trades


```{topic} Outline
In this lecture, we will introduce two new concepts, indifference curves and the marginal rate of substitution.

* [Indifference curves](content:references:indifference-curves) are combinations of choices or fearures that provide a decision-making agent with the same level of utility. Thus, an indiffrence curve is a `isohappiness` curve in the space of possible choices (or features). 

* [The marginal rate of substitution](content:references:marginal-rate-of-sub) is the rate at which a consumer is willing to trade one good for another and remain equally satisfied, i.e., the decision-maker is indifferent between the two choices. The marginal rate of substitution is derived from a local expansion of the utility function around a starting point $x^{\star}\in{X}$, where $X$ is the set of all possible objects.
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

The challenge that we have is to solve for the set of choices that provide the same level of utility. This is difficult because the utility functions are not necessarily linear. Thus, often we cannot simply solve for the set of choices that provide the same level of utility by setting the utility function equal to a constant. 

### Global calculation of indifference
We can recast the calculation of the set of choice (or feartures) that provide the same level of utility as an optimization problem. We can solve for the set of choices that provide the same level of utility by minimizing the objective function:

$$
\begin{equation}
\min_{x}\,\Bigl(U(x^{\star}_{1},\dots,x^{\star}_{m}) - U^{\star}\Bigr)^{2}
\end{equation}
$$

subject to bounds on the choice variables $x_{i}$, i.e., $x_{i}\in{[x_{i,\min},x_{i,\max}]}$. This optimization problem is a least-squares problem, and can be solved using a variety of numerical methods. 


### Local approximation of indifference
Instead, of solving for the global indifference set, we can use a local expansion of the utility function around a starting point $x^{\star}\in{X}$, where $X$ is the set of all possible objects. For some utility function $U:X\rightarrow\mathbb{R}$, the local expansion of the utility function around $x^{\star}$ is given by:

```{math}
dU = \sum_{i\in{1\dots{n}}}\bar{U}_{x_{i}}\cdot{dx_{i}}
```

where $dU\approx\left(U - U_{\star}\right)$ denotes the change in utility, $\bar{U}_{x_{i}}$ denotes the marginal utility of $x_{i}$ evaluated at the starting point, and $dx_{i}\approx(x_{i}-x_{i,\star})$ is the change in $x_{i}$. However, in the local area around $x^{\star}$, the indifference curve has the condition $dU = 0$ which gives:

```{math}
:label: eqn-indifference-curve-local
\sum_{i\in{1\dots{m}}}\bar{U}_{x_{i}}\cdot{dx_{i}} = 0
```

which we can rearrange to get for any $i-j$ pair (all else held constant):

```{math}
:label: eqn-indifference-curve-local-pair
x_{i} \simeq x^{\star}_{i} - \frac{\bar{U}_{x_{i}}}{\bar{U}_{x_{j}}}\left(x_{j} - x^{\star}_{j}\right)\qquad{\forall{i\neq{j}}}
```



(content:references:marginal-rate-of-sub)=
## Marginal Rate of Substitution
The marginal rate of substitution describes the rate at which a consumer is willing to trade one good (or feature) for another. We can derive the marginal rate of substitution from the local expansion of the utility function around a starting point $x^{\star}\in{X}$, where $X$ is the set of all possible objects. For utility function $U:X\rightarrow\mathbb{R}$, the marginal rate of substitution between any two goods (or features) $x_{i}$ and $x_{j}$ along the indifference curve, i.e., a curve where `dU = 0`, is given by:

```{math}
\bar{U}_{x_{i}}\,dx_{i} = -\bar{U}_{x_{j}}\,dx_{j}\qquad{\forall{i\neq{j}}}
```

or equivalently:

```{math}
\frac{dx_{i}}{dx_{j}} = -\frac{\bar{U}_{x_{j}}}{\bar{U}_{x_{i}}}\qquad{\forall{i\neq{j}}}
```

---

## Summary
In this lecture, we introduced two new concepts, indifference curves and the marginal rate of substitution.

* [Indifference curves](content:references:indifference-curves) are combinations of choices or fearures that provide a decision-making agent with the same level of utility. Thus, an indiffrence curve is a `isohappiness` curve in the space of possible choices (or features). 

* [The marginal rate of substitution](content:references:marginal-rate-of-sub) is the rate at which a consumer is willing to trade one good for another and remain equally satisfied, i.e., the decision-maker is indifferent between the two choices. The marginal rate of substitution is derived from a local expansion of the utility function around a starting point $x^{\star}\in{X}$, where $X$ is the set of all possible objects.