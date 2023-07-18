# Indifference Curves
Indifference curves are combinations of choices that provide a decision-making agent with the same level of utility. Thus, an indiffrence curve is a `iso-happiness` or `iso-satisfaction` curve in the space of choices. They are a key tool in consumer theory, and are used to model the preferences of consumers.

```{topic} Outline
In this lecture, we introduce indifference curves for some common utility functions and discuss the properties of indifference curves, particularly the marginal rate of substitution of each type of utility function. 

* [Indifference curves for perfect substitutes](content:references:indifference-curves-perfect-sub) are linear where a consumer is willing to trade one good for another at a fixed ratio, i.e., the marginal rate of substitution is constant.

* [Indifference curves for perfect complements](content:references:indifference-curves-perfect-complement) are L-shaped where a consumer is willing to either zero or infinite units of one good for a unit of another good, i.e., the marginal rate of substitution is either zero or infinite.

* [Indifference curves for Cobb-Douglas utility functions](content:references:indifference-curves-cobb-douglas) are convex, where a consumer is willing to trade one good for another at a varying ratio, i.e., the marginal rate of substitution is not constant and varies with the amount of each good consumed.
```

---


(content:references:indifference-curves-perfect-sub)=
## Indifference curves for perfect substitutes
[Perfect substitutes](https://en.wikipedia.org/wiki/Substitute_good) are goods that can be used interchangeably. In a collection of perfect substitutes, the utility function is linear, creating constant slope indifference curves. This means a decision-maker is willing to switch between goods at a fixed ratio, and the marginal rate of substitution between perfect substitutes is constant.

```{admonition} Examples of perfect substitutes
* Goods that are very similar from different providers, such as hard drives, memory chips, pens, pencils, etc.
* Electricity from different power plants, which cannot be differentiated by the user
* One dollar bill can be replaced perfectly by another dollar bill
```

### Derivation of Marginal Rate of Substitution
Let’s consider a collection of $n$ goods or services which are perfect substitutes that is governed by the linear utility function $U:X\rightarrow\mathbb{R}$:

```{math}
:label: eqn-linear-utility
U(x_{1},\dots,x_{n}) = \sum_{i\in{1\dots{n}}}\alpha_{i}\cdot{x_{i}}
```

where $\bar{U}_{i}\equiv\alpha_{i}$ is the marginal utility of $U(\dots)$ with respect to good $x_{i}$. Expanding the utility function around an operating point $x^{\star}_{1},\dots,x^{\star}_{n}$ yields:

```{math}
:label: eqn-total-differential-linear-utility
dU = \sum_{i\in{1\dots{n}}}\alpha_{i}\cdot{dx_{i}}
```

However, along a line of constant utility, i.e., an indifference curve, the change in utility is zero: 

```{math}
:label: eqn-total-differential-linear-utility-zero
\sum_{i\in{1\dots{n}}}\alpha_{i}\cdot{dx_{i}} = 0
```

Thus, the marginal rate of substitution between any two substitutable goods $x_{i}$ and $x_{j}$ along the indifference curve is given by:

```{math}
:label: eqn-marginal-rate-substitution-linear-utility
\alpha_{i}dx_{i} = -\alpha_{j}dx_{j}\qquad{\forall{i\neq{j}}}
```

or equivalently:

```{math}
:label: eqn-marginal-rate-substitution-linear-utility-2
\frac{dx_{i}}{dx_{j}} = -\frac{\alpha_{j}}{\alpha_{i}}\qquad{\forall{i\neq{j}}}
```

### Implementation
Fill me in.

(content:references:indifference-curves-perfect-complement)=
## Indifference curves for perfect complements
A [perfect complement](https://en.wikipedia.org/wiki/Complementary_good) is a good or service that must be consumed along with another good. Such preferences can be represented by a [Leontief utility function](https://en.wikipedia.org/wiki/Leontief_utilities) of the form:

```{math}
:label: eqn-leontief-utility
U(x_{1},\dots,x_{n}) = \min\left\{\frac{x_{1}}{w_{1}},\dots,\frac{x_{n}}{w_{n}}\right\}
```

where $w_{i}~(\text{for}~i\in{1\dots{n}})$ is the weight of good $x_{i}$ in the utility function, $x_{i}~(\text{for}~i\in{1\dots{n}})$ is the quantity of good or service $x_{i}$ consumed, and $n$ is the number of goods in the collection. If two goods are [perfect complements](https://en.wikipedia.org/wiki/Complementary_good), then the indifference curves will be L-shaped. 

```{admonition} Example of perfect complements
* Suppose $x_{1}$ is the number of left shoes and $x_{2}$ is the number of right shoes. A consumer can only use pairs of shoes. Thus, their utility is $U(x_{1},x_{2}) = \min\left\{x_{1},x_{2}\right\}$.
```

### Derivation of Marginal Rate of Substitution
Fill me in.

### Implementation
Fill me in.

(content:references:indifference-curves-cobb-douglas)=
## Indifference curves for Cobb-Douglas utility functions
The Cobb–Douglas function is a [utility function](https://en.wikipedia.org/wiki/Utility) over a collection of $n$ goods or services that takes the form:

```{math}
:label: eqn-cobb-douglas-utility
U(x_{1},\dots,x_{n}) = \prod_{i\in{1\dots{n}}}x_{i}^{\alpha_{i}}
```

where the exponents $\alpha_{i}$, also known as the elasticities, are constrained to sum to one:

```{math}
:label: eqn-cobb-douglas-utility-constraint
\sum_{i\in{1\dots{n}}}\alpha_{i} = 1
```

```{admonition} Cobb-Douglas utility functions
* A consumer with Cobb-Douglas preferences will always buy some of each good or service in the collection. 
* The marginal rate of substitution between any two goods or services $x_{i}$ and $x_{j}$ that are governed by the Cobb-Douglas utility is equal to the ratio of prices.
```


### Derivation of Marginal Rate of Substitution
The [Cobb–Douglas utility function](https://en.wikipedia.org/wiki/Cobb–Douglas_production_function) has the marginal utility: 

```{math}
:label: eqn-mu-u-function

\bar{U}_{x_{i}} = \left(\alpha_{i}x^{\alpha_{i}-1}\right)\cdot\left(\prod_{j=1,i}^{n}x_{j}^{\alpha_{j}}\right)
```

### Implementation
Fill me in.

---

## Summary
In this lecture, we introduced indifference curves for some common utility functions and discussed the properties of indifference curves, particularly the marginal rate of substitution of each type of utility function. 

* [Indifference curves for perfect substitutes](content:references:indifference-curves-perfect-sub) are linear where a consumer is willing to trade one good for another at a fixed ratio, i.e., the marginal rate of substitution is constant.

* [Indifference curves for perfect complements](content:references:indifference-curves-perfect-complement) are L-shaped where a consumer is willing to either zero or infinite units of one good for a unit of another good, i.e., the marginal rate of substitution is either zero or infinite.

* [Indifference curves for Cobb-Douglas utility functions](content:references:indifference-curves-cobb-douglas) are convex, where a consumer is willing to trade one good for another at a varying ratio, i.e., the marginal rate of substitution is not constant and varies with the amount of each good consumed.