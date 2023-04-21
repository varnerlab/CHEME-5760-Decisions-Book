# Utility Functions and Rational Choices
Utility functions are mathematical expressions representing an individual's preferences over different choices or outcomes. It assigns a numerical value, called utility which is a surrogate for happiness or satisfaction, to each possible option or outcome, based on how much the individual values it. However, a utility function is subjective and can vary from person to person, as different individuals may have other preferences.

In this lecture, we'll develop tools to compute rational choices and explore some mathematical and philosophical properties of utility functions:

* {ref}`content:references:rational-choice-theory` is a framework that seeks to explain human behavior by assuming that individuals make rational choices based on their preferences and goals. This theory suggests that people are motivated by self-interest and will choose actions that maximize their benefits, i.e., their utility while minimizing their costs.

* {ref}`content:references:indifference-curves` are a tool used in microeconomics to analyze consumers’ preferences. They represent a graphical depiction of different combinations of two goods that provide the same level of satisfaction, or utility, to a consumer. Indifference curves can be used to understand how consumers make choices when faced with trade-offs between goods and how they may respond to changes in prices or income.

---

(content:references:rational-choice-theory)=
## Rational choice theory
[Rational choice theory](https://en.wikipedia.org/wiki/Rational_choice_theory) assumes individuals make rational decisions based on their preferences and available information. [Rational choice theory](https://en.wikipedia.org/wiki/Rational_choice_theory) is based on computing the utility of actions or outcomes. Thus, utility functions are a crucial component of this theory, as they describe how individuals assign values to different results or choices ({prf:ref}`defn-individual-utility`):

````{prf:definition} Ordinal utility function
:label: defn-individual-utility

An individual decision-making agent is presented with a bundle of $n$ objects $x_{1},\dots,x_{n}$. A utility function represents the preference of the agent for combinations of these $n$ objects:

```{math}
:label: eqn-utility-function-generic
U(x_{1},x_{2},\dots,x_{n})
```

The utility function $U(\dots)$ is unique only up to an order-preserving transformation in period $t\rightarrow{t+dt}$. Further, utility functions are ordinal, i.e., they rank-order bundles but do not indicate how much better a bundle is compared to another.

````

{prf:ref}`defn-individual-utility` does not give specifics about the properties of a utility function. However, it does establish a critical concept; the utility can be used to rank order the preference for different choices. For example, suppose we have two choices, $A$ and $B$:

* If $A\succ{B}$, the decision maker _strictly prefers_ $A$ to $B$. Then, the utility of choice $A$ is greater than $B$, or $U(A)>U(B)$.
* If $A\sim{B}$, the decision maker is _indifferent_ between $A$ to $B$. Then, the utility of choice $A$ is the same as $B$, or $U(A)=U(B)$.
* If $A\succsim{B}$, the decision maker _weakly prefers_ $A$ over $B$, or they are indifferent. Then, the utility of choice $A$ is greater than or equal to $B$, or $U(A)\geq{U(A)}$.

### Properties of utility functions
A utility function is a mathematical representation of a person's preferences over different outcomes or alternatives. Here are some properties that a utility function should possess:

* __Completeness__: A utility function should be able to rank all possible outcomes or alternatives. In other words, for any two outcomes, the utility function should tell us which one is preferred or whether they are equally preferred.
* __Transitivity__: If outcome A is preferred to outcome B, and outcome B is preferred to outcome C, then outcome A must be preferred to outcome C. This is known as the transitivity property.
* __Monotonicity__: If more of a good is always preferred to less, then the utility function should increase in that good. Conversely, if less of a bad is always preferred to more, then the utility function should decrease in that bad.
* __Continuity__: Small changes in the outcome or alternatives should result in small changes in the utility function. This is known as the continuity property.
* __Concavity__: The utility function should be concave if the person exhibits diminishing marginal utility. This means that as a person consumes more of a good, the additional satisfaction gained from each unit consumed decreases.

These properties help ensure that a utility function accurately represents a person's preferences and can be used to make rational choices between alternatives.

### Example utility functions
There are many different classes of utility functions, let's look at a few examples and examine there properties:

* __Logarithmic utility function__ assumes that an individual's utility is a function of the logarithm of the quantity consumed, and is represented by the equation $U(x) = ln(x)$.
* __Quadratic utility function__ assumes that an individual's utility is proportional to the square of the quantity consumed, and is represented by the equation $U(x) = ax^{2}$, where $a>0$ is a positive constant.
* __Exponential utility function__ assumes that an individual's utility is proportional to the exponential of the quantity consumed, and is represented by the equation $U(x) = e^{ax}$, where $a>0$ is a positive constant.
* __Linear utility function__ assumes that an individual's utility is directly proportional to the quantity consumed, and is represented by the equation $U(x) = \sum{a_{i}x_{i}}$, where $a_{i}>0$ is a positive constant.
* __Cobb-Douglas utility function__ is commonly used in economics and assumes that an individual's utility is a function of the quantity of two or more goods consumed, and is represented by the equation $U(x_{1},\dots,x_{n}) = \prod{x_{i}^{\alpha_{i}}}$, where $\alpha_{i}>0$ are positive constants.
* __Leontief utility function__ assumes that an individual's utility is based on the minimum amount of each attribute or variable required to achieve a certain level of satisfaction. The function is represented by the equation $U(x_{1},\dots, x_{n}) = \min\left\{\alpha_{1}x_{1},\dots,\alpha_{n}x_{n}\right\}$, where $\alpha_{i}$ are the minimum amounts required for each variable, and $x_{i}$ are the quantities consumed.

(content:references:indifference-curves)=
## Indifference curves
Indifference curves are graphical representations of combinations of choices that provide a decision-making agent with the same level of utility ({numref}`fig-cobb-douglas-ic`). Thus, decision-makers are _indifferent_ to the consumption of different combinations of goods (or services) on an indifference curve. 

 ```{figure} ./figs/Fig-CobbDouglas-IndifferenceCurves-Sqrt.pdf
---
height: 400px
name: fig-cobb-douglas-ic
---
Two-dimensional indifference curves were generated using the Cobb–Douglas utility function with $\alpha_{1} = \alpha_{2} = 0.5$. The decision maker is indifferent to a choice between point $A$ and $B$, i.e., $A\sim{B}$ or $C\sim{D}$. However, the decision maker strictly prefers $C$ and $D$ compared to $A$ and $B$, i.e., $C\sim{D}\succ{A}\sim{B}$.
```

For example, the decision agent with the Cobb–Douglas utility function shown in ({numref}`fig-cobb-douglas-ic`) is _indifferent_ to a choice between $A$ and $B$, but strictly prefers $C$ and $D$ to either $A$ or $B$. 

Sample code to compute the two-dimensional indifference curve for a Cobb–Douglas utility function with $\alpha_{1} = \alpha_{2} = 0.5$:
```julia
# initialize
α₁ = 0.5 
α₂ = 1.0 - α₁

# Storage: holds indifference curves 
results = Dict{Int64,Array{Float64,2}}()

# Set values for the good and service 1
X1 = range(0.001,stop=100.0,step = 0.001) |> collect;
d = length(X1);

# Set utility values
U = [12.0, 24.0, 36.0, 48.0];
n = length(U);

# simulation loop
for i ∈ 1:n

    # Allocate storage for the indifference curve 
    Y = Array{Float64,2}(undef,d,2);
    U_val = U[i];

    # compute X2 from the X1 values
    for j ∈ 1:d

        # compute the log-transformed utility
        tmp = (1/α₂)*(log(U_val) - α₁*log(X1[j]));

        # store
        Y[j,1] = X1[j];
        Y[j,2] = exp(tmp); # inverse transform
    end

    # store -
    results[i] = Y;
end
```
---

# Summary
In this lecture, we'll developed tools to compute rational choices and explored some mathematical and philosophical properties of utility functions:

* {ref}`content:references:rational-choice-theory` is a framework that seeks to explain human behavior by assuming that individuals make rational choices based on their preferences and goals. This theory suggests that people are motivated by self-interest and will choose actions that maximize their benefits, i.e., their utility while minimizing their costs.

* {ref}`content:references:indifference-curves` are a tool used in microeconomics to analyze consumers’ preferences. They represent a graphical depiction of different combinations of two goods that provide the same level of satisfaction, or utility, to a consumer. Indifference curves can be used to understand how consumers make choices when faced with trade-offs between goods and how they may respond to changes in prices or income.