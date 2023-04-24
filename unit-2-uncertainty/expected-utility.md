# Rational Uncertain Decisions
Previously, we developed tools to make optimal choices when the outcomes were sure, and the level of satisfaction derived from those choices was known, e.g., the utility of purchasing a particular bundle of goods or services could be computed using a utility function. However, in many real-world situations, the assumption of certainty is invalid. For example, betting, buying an insurance policy, investing in a new business, or the stock market all or _uncertain_. 

Toward understanding how to make uncertain rational decisions, we begin by introducing the [von Neumann-Morgenstern theorem](https://en.wikipedia.org/wiki/Von_Neumann–Morgenstern_utility_theorem) and then discuss two versions of the uncertain rational decision problem:

* {ref}`content:references:vnm-theorem` is a fundamental concept in decision theory that provides a mathematical foundation for expected utility theory. It states that if an individual's preferences over uncertain outcomes satisfy certain axioms, then there exists a utility function that represents those preferences. This theorem has important implications for understanding how people make decisions under uncertainty and designing mechanisms to elicit and aggregate individual preferences.

* {ref}`content:references:cont-util-prob` involve a decision-making agent deciding between continuous objects, i.e., choices between infinitely divisible goods, services, lotteries, etc subject to various types of constraints, i.e., budget constraints.

* {ref}`content:references:disc-util-prob` involve the decision marker making integer or binary decisions, e.g., should they pack an umbrella on a trip. In these cases, the world is divided into a set of states $\mathcal{S}$, the agent makes observations from the set $\mathcal{O}$ and takes actions from the set $\mathcal{A}$.

---

(content:references:vnm-theorem)=
## The von Neumann-Morgenstern theorem
The [von Neumann-Morgenstern theorem](https://en.wikipedia.org/wiki/Von_Neumann–Morgenstern_utility_theorem), the basis for the [expected utility hypothesis](https://en.wikipedia.org/wiki/Expected_utility_hypothesis), is a fundamental result in decision theory that provides a framework for making _rational choices_ under uncertainty {cite}`vonneumann1947`. 

The [von Neumann-Morgenstern theorem](https://en.wikipedia.org/wiki/Von_Neumann–Morgenstern_utility_theorem) posits, under certain axioms of rational behavior, that an agent faced with probabilistic outcomes will behave as if they are maximizing the expected value of a utility function, potentially subject to various types of constraints, e.g., budget constraints or other restrictions concerning how the world works. 

The rationality of the [von Neumann-Morgenstern theorem](https://en.wikipedia.org/wiki/Von_Neumann–Morgenstern_utility_theorem) is based on three axioms:

* __Completeness__: The decision maker can always compare any two alternatives and determine which one is preferred or declare them equally preferred.
* __Transitivity__: If alternative A is preferred to alternative B, and alternative B is preferred to alternative C, then alternative A must be preferred to alternative C.
* __Independence__: The utility of an alternative should depend only on the consequences and not on how the decision maker arrived at that alternative. Specifically, if alternatives A and B have the same values, the decision maker should be indifferent between them, regardless of how the choice was presented or framed.
<!-- 
The VNM utility theorem shows that any individual who follows these axioms must have a utility function that can be used to evaluate and compare alternatives and that a unique probability distribution over outcomes can represent this utility function. -->

The decision variables that a utility-maximizing agent makes decisions over can be either continuous or discrete. In both the continuous and discrete cases, the [expected utility hypothesis](https://en.wikipedia.org/wiki/Expected_utility_hypothesis) depends upon an understanding of two critical concepts, [random variables and probability](../appendix/appendix-landing.md). For students uncomfortable with these topics, please consult the [appendicies](../appendix/appendix-landing.md) of these notes. 

(content:references:cont-util-prob)=
## Continuous expected utility problems
In the continuous utility problem, a decision-making agent is deciding between continuous objects, i.e., choices between an infinitely divisible good or service subject to constraints, i.e., budget constraints ({prf:ref}`defn-expected-utility-hypothesis-cont`): 

````{prf:definition} Continuous expected utility hypothesis
:label: defn-expected-utility-hypothesis-cont

An agent chooses amongst $n$ possible uncertain objects, $x_{1},\dots,x_{n}$ where object $x_{k}\in\mathbb{R}$ has a probability $p_{k}$ of occuring and a utility payoff of $U(x_{k})$. A _rational decision-maker_ maximizes the expected utility subject to constraints:


```{math}
:label: eqn-max-expected-ulity-problem

\begin{eqnarray}
\text{maximize}~\mathbb{E}(x) &=& \sum_{k=1}^{n}p_{k}U(x_{k}) \\
\text{subject to}~g(x)~& \leq & 0\\
\text{and}~x_{k}&\geq&{0}\qquad{k=1,2,\dots,n}
\end{eqnarray}

```

The constrint $g(x)$ denotes potentially non-linear constraints governing the objects $x_{1},\dots,x_{n}$.
````

(content:references:disc-util-prob)=
## Discrete expected utility problems
In discrete problems, the decision marker is making integer or binary decisions, e.g., should they pack an umbrella on a trip. In these cases, 
the world exists in states $\mathcal{S}$, agents make observations $\mathcal{O}$ and take actions $\mathcal{A}$.  The utility of state $s\in\mathcal{S}$, described by $U(s)$, where the utility function $U$ follows the [properties of the utility functions](https://varnerlab.github.io/CHEME-5760-Decisions-Book/unit-1-simpledecisions/utilityfunctions.html#properties-of-utility-functions). Further, an agent makes observations $o\in\mathcal{O}$ and takes actions $a\in\mathcal{A}$. Then, a rational agent solves the expected utility problem ({prf:ref}`defn-expected-utility-hypothesis-discrete`):

````{prf:definition} Discrete expected utility problem
:label: defn-expected-utility-hypothesis-discrete

An agent has a model $P(s^{\prime}|o,a)$, which represents the probability of the world being in state $s^{\prime}$ given that the agent observes $o$ and takes action $a$. The payoff of state $s^{\prime}$ is given by $U(s^{\prime})$. A _rational agent_ maximizes the expected utility subject to constraints:

```{math}
:label: eqn-max-expected-ulity-problem-discrete

\begin{eqnarray}
\text{maximize}~\mathbb{E}(s) &=& \sum_{s^{\prime}}P(s^{\prime}|a,o)U(s^{\prime}) \\
\text{subject to}~s^{\prime} &=& T(s,a) \\
\text{and}~s&\in&\mathcal{S} \\
\text{and}~a&\in&\mathcal{A} \\
\text{and}~o&\in&\mathcal{O} \\
\end{eqnarray}

```

where $T(s,a)$ denotes a transition function governing the transition from state $s\rightarrow{s^{\prime}}$ under action $a$.  

````



---

# Summary
Toward understanding uncertain rational decisions, in this lecture we introduced the [von Neumann-Morgenstern theorem](https://en.wikipedia.org/wiki/Von_Neumann–Morgenstern_utility_theorem) and then discussed two versions of the uncertain rational decision problem:

* {ref}`content:references:vnm-theorem` is a fundamental concept in decision theory that provides a mathematical foundation for expected utility theory. It states that if an individual's preferences over uncertain outcomes satisfy certain axioms, then there exists a utility function that represents those preferences. This theorem has important implications for understanding how people make decisions under uncertainty and designing mechanisms to elicit and aggregate individual preferences.

* {ref}`content:references:cont-util-prob` involve a decision-making agent deciding between continuous objects, i.e., choices between infinitely divisible goods, services, lotteries, etc subject to various types of constraints, i.e., budget constraints.

* {ref}`content:references:disc-util-prob` involve the decision marker making integer or binary decisions, e.g., should they pack an umbrella on a trip. In these cases, the world is divided into a set of states $\mathcal{S}$, the agent makes observations from the set $\mathcal{O}$ and takes actions from the set $\mathcal{A}$.