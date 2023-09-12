# Rational Uncertain Decisions
Previously, we developed tools to make optimal choices when the outcomes were sure, and the level of satisfaction derived from those choices was known, e.g., the utility of purchasing a particular bundle of goods or services could be computed using a utility function. However, in many real-world situations, the assumption of certainty is invalid. For example, betting, buying an insurance policy, investing in a new business, or the stock market all or _uncertain_. 

```{topic} Outline
This lecture explores decisions in an uncertain world. We’ll introduce the von Neumann-Morgenstern theorem, explore two versions of the uncertain rational decision problem, and introduce some concepts from probability theory.

* {ref}`content:references:vnm-theorem` is a fundamental concept in decision theory that provides a mathematical foundation for expected utility theory. It states that if an individual's preferences over uncertain outcomes satisfy certain axioms, a utility function exists that represents those preferences. This theorem has important implications for understanding how people make decisions under uncertainty and designing mechanisms to elicit and aggregate individual preferences.

* [Continuous expected utility problems](content:references:cont-util-prob) involve a decision-making agent deciding between continuous objects, i.e., choices between infinitely divisible goods, services, lotteries, etc., subject to constraints, i.e., budget or other resource constraints. On the other hand, [discrete expected utility problems](content:references:disc-util-prob) involve the decision marker making decisions in a discrete world divided into states $\mathcal{S}$, observations $\mathcal{O}$ and actions 
$\mathcal{A}$.

* Finally, we'll introduce some [basic concepts from probability theory](content:references:prob-basics). In particular, the expected value, variance, and probability mass functions for some common discrete random variables.

```

---

(content:references:vnm-theorem)=
## The von Neumann-Morgenstern theorem
The [von Neumann-Morgenstern theorem](https://en.wikipedia.org/wiki/Von_Neumann–Morgenstern_utility_theorem), which forms the basis for the expected utility hypothesis, is a crucial concept in decision theory. It provides a framework for making rational choices under conditions of uncertainty {cite}`vonneumann1947`. According to this theorem, when faced with probabilistic outcomes, an agent will behave as if they are maximizing the expected value of a utility function, subject to certain axioms of rationality:

* __Completeness__: The decision maker can always compare any two alternatives and determine which one is preferred or declare them equally preferred.
* __Transitivity__: If alternative A is preferred to alternative B, and alternative B is preferred to alternative C, then alternative A must be preferred to alternative C.
* __Continuity__: If alternative A is preferred to alternative B, then there exists some probability $p$ such that the decision maker is indifferent between a lottery that pays $A$ with probability $p$ and $B$ with probability $1-p$ and alternative B.

<!-- 
The VNM utility theorem shows that any individual who follows these axioms must have a utility function that can be used to evaluate and compare alternatives and that a unique probability distribution over outcomes can represent this utility function. -->

The decision variables that a utility-maximizing agent makes decisions over can be either continuous or discrete.  

(content:references:cont-util-prob)=
### Continuous expected utility problems
In the continuous utility problem, a decision-making agent is deciding between continuous objects, i.e., choices between an infinitely divisible good or service subject to constraints, e.g., budget or other types of resource constraints ({prf:ref}`defn-expected-utility-hypothesis-cont`): 

````{prf:definition} Continuous expected utility hypothesis
:label: defn-expected-utility-hypothesis-cont

An agent has a set of $n$ objects $X = \left\{x_{i}\right\}_{i=1}^{n}$, 
a utility function $U:X\rightarrow\mathbb{R}$, and a total of $I$ units of resource to allocate, e.g., money, time, etc. 
Each object $x_{i}$ has a unit cost of $c_{i}\geq{0}$, a probability $p_{i}$ of occuring.
A rational decision-maker maximizes the [expected utility](https://en.wikipedia.org/wiki/Expected_utility_hypothesis) 
subject to constraints:

$$
\begin{eqnarray*}
\text{maximize}~\mathbb{E}(x) &=& \sum_{k\in{1,\dotsc,n}}p_{k}U(x_{k}) \\
\text{subject to}~g(x)~& \leq & 0\\
\text{and}~x_{k}&\geq&{0}\qquad{k=1,2,\dots,n}
\end{eqnarray*}
$$

where $\mathbb{E}(x)$ is the [expectation](https://en.wikipedia.org/wiki/Expected_value) computed 
over the possible alternatives, $g(x)$ is a constraint function, and $x_{k}\geq{0}$ represents the amount of object $k$ purchased or consumed by the agent.
````

(content:references:disc-util-prob)=
### Discrete expected utility problems
In discrete problems, the decision marker is making integer or binary decisions, e.g., should they pack an umbrella on a trip. In these cases, the world exists in states $\mathcal{S}$, agents make observations $\mathcal{O}$ and take actions $\mathcal{A}$. Rational agents in this type of world solves the discrete expected utility problem ({prf:ref}`defn-expected-utility-hypothesis-discrete`):

````{prf:definition} Discrete expected utility problem
:label: defn-expected-utility-hypothesis-discrete

The world is divided into states $\mathcal{S}$, where agents make observations $\mathcal{O}$ and take actions $\mathcal{A}$. 
Each state $s\in\mathcal{S}$ has a value determined by a utility function $U:\mathcal{S}\rightarrow\mathbb{R}$. 
Rational agents maximize their expected utility:

$$
\begin{eqnarray*}
\text{maximize}~\mathbb{E}(U(a|o,s)) &=& \sum_{s^{\prime}}P(s^{\prime}|a,o,s)U(s^{\prime}) \\
\text{subject to}~\sum_{s^{\prime}} P(s^{\prime}|a,o,s) & = & 1
\end{eqnarray*}
$$

where $s\in\mathcal{S}$, $a\in\mathcal{A}$, $o\in\mathcal{O}$ and $P(s^{\prime}|a,o,s)$ is the probability of being in state 
$s^{\prime}$ after observing $o$ and taking action $a$. The principle of maximum expected utility says that a rational agent should choose the action that maximizes expected utility:

$$
\begin{equation*}
a^{\star} = \text{arg}\max_{a} \mathbb{E}(U(a|o,s))
\end{equation*}
$$  
````

(content:references:prob-basics)=
## Probability basics
Both the problems of continuous and discrete utility that were mentioned before are used to model decisions made in an uncertain world. Whenever there is uncertainty involved, probability can be utilized to model it. This section will cover some fundamental concepts from probability theory, with a focus on two crucial concepts - random variables and the behavior and properties of probability mass (distribution) functions.

* A [random variable](https://en.wikipedia.org/wiki/Random_variable) is a variable $X$ that takes on different values $x$ according to the outcome of a random event or process. There are two types of random variables: discrete random variables and continuous random variables. Discrete random variables can take on a countable number of distinct values, while continuous random variables can take on any value in a continuous range. 
* [Probability](https://en.wikipedia.org/wiki/Probability) measures the likelihood that a particular event or outcome will occur and is commonly used to quantify uncertainty in various fields, such as science, engineering, economics, and finance. For a discrete random variable, the likelihood that $X=x$ is described by a [Probability Mass Function (PMF)](https://en.wikipedia.org/wiki/Probability_mass_function) and a [Probability Density Function (PDF)](https://en.wikipedia.org/wiki/Probability_density_function) for continuous random variables.  

### Probability spaces
A [probability space](https://en.wikipedia.org/wiki/Probability_space) is a mathematical construct that models a real-world situation where there is uncertainty. A probability space is completely described by the tuple $(\Omega,\mathcal{F},P)$:
* Sample space $\Omega$: The set of all possible outcomes from an experiment.
* Event space $\mathcal{F}$: The collection of all possible events. An event $E$ is a subset in $\Omega$ that defines an outcome or a combination of outcomes that we are interested in.
* Probability law $P$: A mapping from an event $A$ to a number $P(A)$ which, measures the size of the event. The probability function $P$ returns a number between `0` and `1`. If $P(A)=1$, then the event $A$ is certain to occur. If $P(A)=0$, then the event $A$ is impossible to occur.

### Random variables
A [random variable](https://en.wikipedia.org/wiki/Random_variable) $X$ is a variable whose values are numerical outcomes of a random phenomenon. There are two types of random variables: `discrete` and `continuous` random variables.

* A `discrete` random variable takes on only a countable number of distinct values, i.e., $0,1,2,3,4,\dots$.
    * If a random variable take only a finite number of distinct values, it is discrete.
    * The probability of observing a specific value is non-negative.
* A `continuous` random variable takes an infinite number of possible values. 
    * A continuous random variable is not defined at specific values. Instead, it is defined over an interval of values and is represented by the area under a curve.
    * The probability of observing any single value is equal to zero since the number of values that may be assumed by the random variable is infinite.

### Expectation
Let $X$ denote a discrete random variable with the probability space $\left(\Omega,\mathcal{F},P\right)$.  The expected value of the random variable $X$ is given by:

$$
\begin{equation*}
\mathbb{E}\left[X\right] = \sum_{x\in\Omega}x\cdot{p}_{X}(x)
\end{equation*}
$$

where $x$ denotes a value for the discrete random variable $X$, and $p_{X}(x)$ denotes the probability of $X=x$. The expectation of a random variable $X$ has the properties: 

* $\mathbb{E}\left(c\right) = c$ for a constant $c$
* $\mathbb{E}\left(cX\right) = c\times\mathbb{E}\left(X\right)$ for a constant $c$
* $\mathbb{E}\left(g(X)\right) = \sum_{x\in{X(\Omega)}}g(x)p_{X}(x)$
* $\mathbb{E}\left(g(X)+h(X)\right) = \mathbb{E}(g(X)) + \mathbb{E}(h(X))$
* $\mathbb{E}\left(X+c\right) = \mathbb{E}(X) + c$ for a constant $c$

### Variance
Let $X$ denote a discrete random variable with the probability space $\left(\Omega,\mathcal{F},P\right)$.
Then, the variance of the random variable $X$ is given by:

$$
\begin{equation*}
\text{Var}(X) = \mathbb{E}\Bigl[(X-\mu)^{2}\Bigr]
\end{equation*}
$$

where $\mu = \mathbb{E}(X)$ denotes the expected value of the random variable $X$. The variance of a random variable $X$ has a few interesting (and important) properties:
* $\text{Var}(X) = \mathbb{E}\left(X^{2}\right) - \mathbb{E}\left(X\right)^2$
* $\text{Var}(cX) = {c^2}\text{Var}(X)$ for a constant $c$
* $\text{Var}(X+c) = \text{Var}(X)$ for a constant $c$

### Probability mass functions
The probability mass function (PMF) of a discrete random variable $X$ is a function that specifies the probability of obtaining $X = x$, where $x$  is a particular event in the set of possible events we're interested 
in $\mathcal{F}\subseteq{X\left(\Omega\right)}$:

$$
\begin{equation*}
p_{X}(x) = P\left(X=x\right)
\end{equation*}
$$

where $\mathcal{F}$ is the event space, and $\Omega$ is the sample space. A probability mass function must satisfy the condition: 

$$
\begin{equation*}
\sum_{x\in{X(\Omega)}}p_{X}(x)=1
\end{equation*}
$$


In [Julia](https://julialang.org), probability mass (or density) functions can be constructed and sampled using the [Distributions.jl](https://juliastats.org/Distributions.jl/stable/) package. Let's look at a few common probability mass functions.

#### Bernoulli distribution
[Bernoulli random variables](https://en.wikipedia.org/wiki/Bernoulli_distribution), named after the Swiss mathematician [Jacob Bernoulli](https://en.wikipedia.org/wiki/Jacob_Bernoulli), have two states: either `1` or `0` and model binary events such as coin flips, binary bits, true or false, yes or no, present or absent, etc. ({prf:ref}`defn-pmf-bernouli-random-variable`):

````{prf:definition} Bernoulli Random Variable
:label: defn-pmf-bernouli-random-variable

A Bernoulli random variable $X$ models a binary outcome: either `1` or `0`, 
where `1` occurs with probability $p$ and `0` occurs with probability $1-p$. 
The probability mass function (pmf) of the Bernoulli random variable $X$ is:

$$
\begin{equation}
p_{X}(x) = \begin{cases}
    p & \text{if } x = 1 \\
    1 - p & \text{if } x = 0
  \end{cases}
\end{equation}
$$

where $0<p<1$ is called the Bernoulli parameter. The expectation a Bernoulli random variable equals:

$$
\begin{equation}
\mathbb{E}\left[X\right] = p
\end{equation}
$$

while the variance $\text{Var}(X)$ equals:

$$
\begin{equation}
\text{Var}\left[X\right] = p(1-p)
\end{equation}
$$
````

Example code for a [Bernoulli random variable](https://en.wikipedia.org/wiki/Bernoulli_distribution):

```julia
# load the distributions package, and some other stuff
using Distributions
using Statistics
using PrettyTables

# Details of Bernoulli distribution: 
# https://juliastats.org/Distributions.jl/stable/univariate/#Discrete-Distributions

# setup constants -
p = 0.64;
number_of_samples = 100;

# build a Bernoulli distribution
d = Bernoulli(p)

# sample (check expectation, and variance)
samples = rand(d,number_of_samples);

# build a table -
data_for_table = Array{Any,2}(undef, 2, 3)
table_header = ["", "E(X)", "Var(X)"]

# row 1: model
data_for_table[1,1] = "model"
data_for_table[1,2] = mean(d);
data_for_table[1,3] = var(d);

# row 2: samples
data_for_table[2,1] = "samples"
data_for_table[2,2] = mean(samples);
data_for_table[2,3] = var(samples);
pretty_table(data_for_table, header=table_header);
```

#### Geometric distribution
[Geometric random variables](https://en.wikipedia.org/wiki/Geometric_distribution) model the number of trials required to obtain the first success in a sequence of independent Bernoulli trials ({prf:ref}`defn-pmf-geometric-random-variable`):

````{prf:definition} Geometric Random Variable
:label: defn-pmf-geometric-random-variable

Geometric random variables model the number of trials required  to obtain the first success in a sequence of independent Bernoulli trials.  The probability mass function for a geometric random variable is given by:

$$
\begin{equation*}
p_{X}(k) = (1-p)^{(k-1)}p\qquad{k=1,2,\dots}
\end{equation*}
$$

where $p$ denotes the geometric parameter $0<p<1$. The expectation of a geometric random variable $X$ is given by:

$$
\begin{equation*}
\mathbb{E}\left[X\right] = \frac{1}{p}
\end{equation*}
$$

while the variance $\text{Var}(X)$ is given by:

$$
\begin{equation*}
\text{Var}\left[X\right] = \frac{1-p}{p^2}
\end{equation*}
$$

````

Example code for a [Geometric random variables](https://en.wikipedia.org/wiki/Geometric_distribution):

```julia
# load the distributions package, and some other stuff
using Distributions
using Statistics
using PrettyTables

# Details of Geometric distribution: 
# https://juliastats.org/Distributions.jl/stable/univariate/#Distributions.Geometric

# setup constants -
p = 0.64;
number_of_samples = 100;

 # build a Geometric distribution
d = Geometric(p)

# sample (check expectation, and variance)
samples = rand(d, number_of_samples);

# build a table -
data_for_table = Array{Any,2}(undef, 2, 3)
table_header = ["", "E(X)", "Var(X)"]

# row 1: model
data_for_table[1,1] = "model"
data_for_table[1,2] = succprob(d);
data_for_table[1,3] = var(d);

# row 2: samples
data_for_table[2,1] = "samples"
data_for_table[2,2] = mean(samples);
data_for_table[2,3] = var(samples);
pretty_table(data_for_table, header=table_header);
```

#### Binomial distribution
The [binomial distribution](https://en.wikipedia.org/wiki/Binomial_distribution) is the probability of getting $k$ successes in $n$ independent Bernoulli trials, e.g., the chance of getting four heads in six coin tosses ({prf:ref}`defn-pmf-binomial-random-variable`):


````{prf:definition} Binomial Random Variable
:label: defn-pmf-binomial-random-variable

The binomial distribution, the probability of $k$ successes in $n$ independent Bernoulli trials, has the 
probability mass function:

$$
\begin{equation*}
p_{X}(k) = \binom{n}{k}p^{k}\left(1-p\right)^{n-k}\qquad{k=0,1,\dots,n}
\end{equation*}
$$

where $k$ denotes the number of successes in $n$ independent experiments, the binomial parameter $0<p<1$ is the probability 
of a successful trial and:

$$
\begin{equation*}
\binom{n}{k} = \frac{n!}{k!\left(n-k\right)!}
\end{equation*}
$$

is the binomial coefficient. The expectation and variance of a binomial random variable is given by:

$$
\begin{eqnarray*}
\mathbb{E}\left[X\right] &=& np\\
\text{Var}\left[X\right] &=& np(1-p)
\end{eqnarray*}
$$

````

Example code for a [binomial random variable](https://en.wikipedia.org/wiki/Binomial_distribution):


```julia
# load the distributions package, and some other stuff
using Distributions
using Statistics
using PrettyTables

# Details of Binomial distribution: 
# https://juliastats.org/Distributions.jl/stable/univariate/#Distributions.Binomial

# setup constants -
number_of_trials = 100;
p = 0.64;
number_of_samples = 100;

# build a Bernoulli distribution
d = Binomial(number_of_trials,p)

# sample (check expectation, and variance)
samples = rand(d,number_of_samples);

# build a table -
data_for_table = Array{Any,2}(undef, 2, 3)
table_header = ["", "E(X)", "Var(X)"]

# row 1: model
data_for_table[1,1] = "model"
data_for_table[1,2] = mean(d);
data_for_table[1,3] = var(d);

# row 2: samples
data_for_table[2,1] = "samples"
data_for_table[2,2] = mean(samples);
data_for_table[2,3] = var(samples);
pretty_table(data_for_table, header=table_header);
```

#### Poisson distribution
[Poisson random variables](https://en.wikipedia.org/wiki/Poisson_distribution) are a type of discrete probability distribution that models the number of occurrences of an event in a fixed interval of time or space ({prf:ref}`defn-pmf-poisson-random-variable`):


````{prf:definition} Poisson Random Variable
:label: defn-pmf-poisson-random-variable

Poisson random variables model the number of occurrences of an event in a fixed interval of time or space.
The probability mass function for a Poisson random variable is given by:

$$
\begin{equation*}
p_{X}(x) = \frac{\lambda^{x}}{x!}\exp\left(-\lambda\right)
\end{equation*}
$$

where $\lambda>0$ denotes the Poisson parameter, and $!$ denotes the factorial function. The expectation of a Poisson random variable $X$ is given by:

$$
\begin{equation*}
\mathbb{E}\left[X\right] = \lambda
\end{equation*}
$$

while the variance $\text{Var}(X)$ is given by:

$$
\begin{equation*}
\text{Var}\left[X\right] = \lambda
\end{equation*}
$$
````

Example code for a [Poisson random variable](https://en.wikipedia.org/wiki/Poisson_distribution):

```julia

# load the distributions package, and some other stuff
using Distributions
using Statistics
using PrettyTables

# Details of Poisson distribution:
# https://juliastats.org/Distributions.jl/stable/univariate/#Distributions.Poisson

# build a Poisson distribution
d = Poisson(λ)

# sample (check expectation, and variance)
samples = rand(d, number_of_samples);

# build a table -
data_for_table = Array{Any,2}(undef, 2, 3)
table_header = ["", "E(X)", "Var(X)"]

# row 1: model
data_for_table[1,1] = "model"
data_for_table[1,2] = mean(d);
data_for_table[1,3] = var(d);

# row 2: samples
data_for_table[2,1] = "samples"
data_for_table[2,2] = mean(samples);
data_for_table[2,3] = var(samples);
pretty_table(data_for_table, header=table_header);
```

---

# Summary
Toward understanding uncertain rational decisions, in this lecture, we introduced the [von Neumann-Morgenstern theorem](https://en.wikipedia.org/wiki/Von_Neumann–Morgenstern_utility_theorem), discussed two versions of the uncertain rational decision problem and introduced some basic concepts from probability theory. In particular, we discussed:

* {ref}`content:references:vnm-theorem` is a fundamental concept in decision theory that provides a mathematical foundation for expected utility theory. It states that if an individual's preferences over uncertain outcomes satisfy certain axioms, a utility function exists that represents those preferences. This theorem has important implications for understanding how people make decisions under uncertainty and designing mechanisms to elicit and aggregate individual preferences.

* [Continuous expected utility problems](content:references:cont-util-prob) involve a decision-making agent deciding between continuous objects, i.e., choices between infinitely divisible goods, services, lotteries, etc., subject to constraints, i.e., budget or other resource constraints. On the other hand, [discrete expected utility problems](content:references:disc-util-prob) involve the decision marker making decisions in a discrete world divided into states $\mathcal{S}$, observations $\mathcal{O}$ and actions 
$\mathcal{A}$.

* Finally, we introduced some [basic concepts from probability theory](content:references:prob-basics). In particular, the expected value, variance, and probability mass functions for some common discrete random variables.