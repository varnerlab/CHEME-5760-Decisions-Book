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
If a set of goods are [perfect substitutes](https://en.wikipedia.org/wiki/Substitute_good) then the indifference curve will have a constant slope since the consumer would be willing to switch between the goods at a fixed ratio. The marginal rate of substitution between perfect substitutes is likewise constant. Let's consider a collection of goods or services $\dim\mathcal{X} = n$ which are perfect substitutes that is governed by linear the utility function $U:\mathcal{X}\rightarrow\mathbb{R}$:

```{math}
U(x) = \sum_{x_{i}\in\mathcal{X}}\alpha_{x_{i}}\cdot{x_{i}}
```

where $\alpha_{x_{i}}$ is the marginal utility of $x_{i}$. Then, the marginal rate of substitution between any two goods $x_{i}$ and $x_{j}$ is constant along the indifference curve (line of constant utility):

```{math}
\sum_{x_{i}\in\mathcal{X}}\alpha_{x_{i}}\cdot{dx_{i}} = 0
```

where $dx_{i}$ is the change in the consumption of good or service $x_{i}$. Thus, the marginal rate of substitution between any two goods $x_{i}$ and $x_{j}$ is constant along the indifference curve:

```{math}
\alpha_{x_{i}}dx_{i} = -\alpha_{x_{j}}dx_{j}\qquad{\forall{i\neq{j}}}
```

or equivalently:

```{math}
\frac{dx_{i}}{dx_{j}} = -\frac{\alpha_{x_{j}}}{\alpha_{x_{i}}}
```

### Implementation
Fill me in.

(content:references:indifference-curves-perfect-complement)=
## Indifference curves for perfect complements
If two goods are [perfect complements](https://en.wikipedia.org/wiki/Complementary_good), then the indifference curves will be L-shaped. Examples of perfect complements include left shoes compared to right shoes: the consumer is no better off having several right shoes if she has only one left shoe - additional right shoes have zero marginal utility without more left shoes, so bundles of goods differing only in the number of right shoes they include - however many - are equally preferred. The marginal rate of substitution is either zero or infinite. 

(content:references:indifference-curves-cobb-douglas)=
## Indifference curves for Cobb-Douglas utility functions
Fill me in.

---

## Summary 
Fill me in