# Risk and Risk Aversion
Risk aversion in decision making refers to the tendency of individuals to prefer options with lower levels of uncertainty or potential loss. When faced with choices, risk-averse individuals prioritize minimizing potential risks over maximizing potential gains. This cognitive bias can influence various aspects of decision making, such as investment choices, career decisions, and even personal choices involving health and safety.

```{topic} Outline

This week we discuss risk, risk aversion, and its role in decisions:

* {ref}`content:references:risk-aversion` is important for understanding how people choose between safe and risky options. This knowledge can help decision-makers develop strategies that match people’s risk preferences.

* {ref}`content:references:measuring-risk-aversion` helps us understand risk and decision-making. The model provides insights into how people weigh potential gains and losses in uncertain situations, and aid in developing strategies that align with individuals’ risk preferences.

```

---

(content:references:risk-aversion)=
## Risk aversion
Understanding risk aversion is crucial for evaluating investment preferences, insurance choices, and risk management strategies. It is a fundamental concept that plays a crucial role in decision-making in uncertain situations, and it varies from person to person. 

```{admonition} Coin flip game
:class: attention

Let's explore how an individual responds to a _fair game_. Suppose we are given a choice to participate in a coin-flipping game where you bet on the result of the flip of a _fair coin_:
* __Heads__: If the coin flip gives heads `H`, you win $w$ USD.
* __Tails__: If the coin flip gives tails `T`, you lose $w$ USD 

Because the coin is fair, the expected outcome of this game is `0`. However, how much would you risk, i.e., would you play if $w$ is large?
```


(content:references:measuring-risk-aversion)=
## Arrow-Pratt model
The Arrow-Pratt risk aversion model is a widely used framework in economics and decision theory for measuring and analyzing individuals' risk preferences {cite}`Hanson-1970`. Proposed by economists [Kenneth Arrow](https://en.wikipedia.org/wiki/Kenneth_Arrow) and [John W. Pratt](https://en.wikipedia.org/wiki/John_W._Pratt), this model quantifies the degree of risk aversion by examining how individuals' utility functions respond to changes in wealth and uncertainty {cite}`Pratt-1964`. 

The Arrow-Pratt measures absolute and relative risk aversion, which allows decision-makers to assess the sensitivity of individuals to risk, informing optimal decision-making strategies in various domains, such as finance, insurance, and investment ({prf:ref}`defn-arrow-pratt-model`):

````{prf:definition} Arrow-Pratt model
:label: defn-arrow-pratt-model

Let $U(w)$ be a utility function describing an individuals satisfaction gained from a unit of wealth $w$. Further, let $U(w)$ be at least twice differentiable with respect to the wealth $w$. Then, the absolute risk aversion measure $r(w)$ is defined as:

```{math}
:label: eqn-abs-risk-aversion-model
r(w) = - \frac{U^{\prime\prime}(w)}{U^{\prime}(w)}
```

and the relative risk aversion $\bar{r}(w)$ is defined as:

```{math}
:label: eqn-relative-risk-aversion-model
\bar{r}(w) = - w\cdot\frac{U^{\prime\prime}(w)}{U^{\prime}(w)}
```

where $U^{\prime}(w)$ and $U^{\prime\prime}(w)$ denote the first and second derivative of the utility function with respect to the weath. 
````

---

## Summary
This week we discussed risk, risk aversion, and its role in decisions:

* {ref}`content:references:risk-aversion` is important for understanding how people choose between safe and risky options. This knowledge can help decision-makers develop strategies that match people’s risk preferences.

* {ref}`content:references:measuring-risk-aversion` helps us understand risk and decision-making. The model provides insights into how people weigh potential gains and losses in uncertain situations, and aid in developing strategies that align with individuals’ risk preferences.