# Marginal Rate of Substitution
The marginal utility quantifies the satisfaction gained by an agent from an additional unit of consumption of a good or service. It is the change in utility resulting from the consumption of an additional unit of a good or service.

```{topic} Outline
Fill me in
```

---

(content:references:marginal-utility)=
## Marginal utility
The marginal utility quantifies the satisfaction gained by an agent from an additional unit of consumption of a good or service ({prf:ref}`defn-marginal-utility`):

````{prf:definition} Marginal Utility
:label: defn-marginal-utility

Let $x\in\mathcal{X}$ be a good or service in the set of goods and services $\mathcal{X}$ and $U:\mathcal{X}\rightarrow\mathbb{R}$ be a utility function. The [marginal utility](https://en.wikipedia.org/wiki/Marginal_utility) of $x$ is the partial derivative of $U$ with respect to $x$:

```{math}
\bar{U}_{x} \equiv \left(\frac{\partial{U}}{\partial{x_{i}}}\right)_{\star}
```

where the marginal utility is evaluated at a point $x^{\star}\in\mathcal{X}^{\star}$. The utility function governing the decision maker $U(\dots)$ can be expanded by computing the [total differential](https://en.wikipedia.org/wiki/Differential_of_a_function#Differentials_in_several_variables) around a point $x^{\star}\in\mathcal{X}^{\star}$:

```{math}
:label: eqn-total-differential-ic

dU = \sum_{x\in\mathcal{X}}\bar{U}_{x}\cdot{dx}
```

where $\bar{U}_{x}$ denotes the marginal utility of $x$ and $dx$ denotes the change in the consumption of good or service $x$.
````