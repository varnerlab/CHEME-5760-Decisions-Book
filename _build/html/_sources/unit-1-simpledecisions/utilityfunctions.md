# Utility Functions and Choice Theory

Utility functions are mathematical expressions that show an individual’s preferences for different choices or outcomes. They give a numerical value, known as utility, for each available option or outcome based on the individual’s valuation of it, which is a proxy for happiness or satisfaction. However, utility functions are subjective and can differ from person to person since everyone has different preferences. 

```{topic} Outline
This week, we'll develop tools to compute rational choices using utility functions, and explore some mathematical and philosophical properties of utility functions:

* {ref}`content:references:rational-choice-theory` is a framework that seeks to explain human behavior by assuming that individuals make rational choices based on their preferences and goals. This theory suggests that people are motivated by self-interest and will choose actions that maximize their benefits, i.e., their utility while minimizing their costs.

* {ref}`content:references:marginal-utility` describes the added satisfaction or benefits that a consumer gains from consuming one more unit of a good or service. This theory operates on the premise that the happiness or benefit from each extra unit decreases as a consumer increases the number of units consumed. Marginal utility is crucial in shaping consumer behavior, prices, and market equilibrium.
```

---

(content:references:rational-choice-theory)=
## Rational choice theory
[Rational Choice Theory](https://en.wikipedia.org/wiki/Rational_choice_theory) is founded on the idea that individuals make decisions based on their preferences and the information available to them. This theory involves calculating the utility of various actions or outcomes using a utility function. The utility function is a vital aspect of this theory as it helps in determining how individuals assign numerical values to different options ({prf:ref}`defn-individual-utility`):

````{prf:definition} Ordinal utility function
:label: defn-individual-utility

An individual decision-making agent is presented with a bundle (set) of $n$ objects $X=\left\{x_{1},\dots,x_{n}\right\}$. A utility function represents the preference of the agent for combinations of these $n$ objects:

```{math}
:label: eqn-utility-function-generic
U(x_{1},x_{2},\dots,x_{n}) = u
```

where $u$ is a real number called the utility. The utility function $U:X\rightarrow\mathbb{R}$ is unique only up to an order-preserving transformation in period $t\rightarrow{t+dt}$. Further, utility functions are ordinal, i.e., they rank-order bundles but do not indicate how much better or worse a bundle is compared to another.
````

{prf:ref}`defn-individual-utility` establishes a critical concept; the utility can be used to rank order the preference for different choices. For example, suppose we have two choices, $A\in{X}$ and $B\in{X}$:

* If $A\succ{B}$, the decision maker _strictly prefers_ $A$ to $B$. Then, the utility of choice $A$ is greater than $B$, or $U(A)>U(B)$.
* If $A\sim{B}$, the decision maker is _indifferent_ between $A$ to $B$. Then, the utility of choice $A$ is the same as $B$, or $U(A)=U(B)$.
* If $A\succsim{B}$, the decision maker _weakly prefers_ $A$ over $B$, or they are indifferent. Then, the utility of choice $A$ is greater than or equal to $B$, or $U(A)\geq{U(B)}$.


```{admonition} Key Idea of Rational Choice Theory
When faced with competing alternatives, i.e., different decision outcomes $A$ and $B$, a decision-making agent will _always_ choose the option that maximizes their utility.
```

(content:references:rational-choice-theory-utility-functions)=
### Utility functions
To better understand utility functions, let’s explore them further. Utility functions are utilized to express preferences for various outcomes by assigning a numerical value to each option, which is referred to as `utility` and measured in `utils`. Here are some properties that a utility function should possess:

* __Completeness__: A utility function should be able to rank all possible outcomes or alternatives. In other words, for any two outcomes, the utility function should tell us which one is preferred or whether they are equally preferred.
* __Transitivity__: If outcome A is preferred to outcome B, and outcome B is preferred to outcome C, then outcome A must be preferred to outcome C. 
* __Monotonicity__: If more of a good is always preferred to less, then the utility function should increase in that good. Conversely, if less of a bad is always preferred to more, then the utility function should decrease in that bad.
* __Continuity__: Small changes in the outcome or alternatives should result in small changes in the utility function. 
* __Concavity__: The utility function should be concave if the person exhibits diminishing marginal utility. This means that as a person consumes more of a good, the additional satisfaction gained from each unit consumed decreases.

These properties help ensure that a utility function accurately represents a person's preferences and can be used to make rational choices between alternatives.

It’s important to note that utility functions, or their parameters, are subjective and may differ from one person to another. There are various types of utility functions, and we’ll examine some examples and their characteristics:

* __Linear utility function__ assumes that an individual's utility is directly proportional to the quantity of goods or services consumed, and is represented by the equation $U(x) = \sum{\alpha_{i}x_{i}}$, where $\alpha_{i}>0$ is a positive constant, and $x_{i}$ denotes the quantity of good or service $i$ consumed.
* __Logarithmic utility function__ assumes that an individual's utility is a function of the logarithm of the quantity consumed, and is represented by the equation $U(x) = \ln(\alpha^{T}\cdot{x}+\beta)$, where $\beta>0$ is a positive constant, and $\alpha^{T}\cdot{x}$ is the scalar product of the vector of parameters $\alpha$ and goods or services $x$, where $x_{i}>0$ and $\alpha_{i}>0$.
* __Exponential utility function__ assumes that an individual's utility is proportional to the exponential of the quantity consumed, and is represented by the equation $U(x) = e^{\alpha^{T}\cdot{x}}$, where $\alpha^{T}\cdot{x}$ is the scalar product of the vector of parameters $\alpha$ and the vector of goods or services $x$, where $x_{i}>0$ and $\alpha_{i}>0$.
* __Cobb-Douglas utility function__ is commonly used in economics and assumes that an individual's utility is a function of the quantity of two or more goods consumed, and is represented by the equation $U(x_{1},\dots,x_{n}) = \prod{x_{i}^{\alpha_{i}}}$, where $\alpha_{i}>0$ are positive constants, and $\sum{\alpha_{i}}=1$.
* __Leontief utility function__ assumes that an individual's utility is based on the minimum amount of each attribute or variable required to achieve a certain level of satisfaction. The function is represented by the equation $U(x_{1},\dots, x_{n}) = \min\left\{x_{1}/\alpha_{1},\dots,x_{n}/\alpha_{n}\right\}$, where $\alpha_{i}$ are the minimum amounts required for each variable, and $x_{i}$ are the quantities consumed for variable $i$, or the system state in configuration $i$, etc.

(content:references:rational-choice-theory-utility-functions-linear)=
#### Linear utility functions
A linear utility function is the simplest utility function. It assumes that an individual's utility is directly proportional to the decision outcome, e.g., the quantity of a good or serice consumed, and is represented by: 

```{math}
:label: eqn-linear-utility-function
U(x) = \alpha^{T}\cdot{x}
```

where $\alpha^{T}\cdot{x}$ denotes the dot product (or scalar product) of the vector of parameters $\alpha$ and the vector of goods or services $x$, where $x_{i}\geq{0}$ and $\alpha_{i}>0$. Let's consider a one-dimensional linear utility function for four decision making agents with $\alpha_{1}<\alpha_{2}<\alpha_{3}<\alpha_{4}$ ({numref}`fig-linear-utility-1d`).

 ```{figure} ./figs/Fig-Linear-Utility-Schematic.png
---
height: 380px
name: fig-linear-utility-1d
---
Linear utility function in one dimension as a function of the quantity of good or service consumed and the values of the utility function parameter $\alpha$.
```

* Each agent has a different utility value at the consumption of 75 units of $x$, indicated as points B, C, D, and E. The agent with the highest value of $\alpha$, Agent 4, has the highest utility value at point E, while the one with the lowest value of $\alpha$, Agent 1, has the lowest utility value at point B.
* Despite the difference in absolute utility values among the agents, their preferences remain the same. For instance, Agent 1 strictly prefers $B\succ{A}$
, which means that they would choose to consume 75 units instead of 50 units of $x$. Similarly, Agent 4 strictly prefers $E\succ{F}$.
* A linear utility function has constant [constant marginal utility](https://en.wikipedia.org/wiki/Marginal_utility), meaning the satisfaction gained from each additional $x$ remains constant.

##### Implementation
We used the [VLDecisionsPackage.jl](https://github.com/varnerlab/VLDecisionsPackage.jl) to build a `linear` utility function model,  and then to plot it. The code that produced ({numref}`fig-linear-utility-1d`) is shown below:

```{code-block} julia
:caption: Linear utility function model in Julia
:linenos:

# load packages -
using VLDecisionsPackage
using Plots
using Colors

# setup colors -
colors = Dict{Int,RGB}()
colors[1] = parse(Colorant, "#D81B60")
colors[2] = parse(Colorant, "#1E88E5")
colors[3] = parse(Colorant, "#FFC107")
colors[4] = parse(Colorant, "#004D40")

# setup ranges and parameters -
goods_array = range(0.0,stop=100.0,step=1.0) |> collect;
parameter_value_array = [0.1, 0.2, 0.3, 0.4];

# goods array -
goods_array = range(0.0,stop=100.0,step=1.0) |> collect;
parameter_value_array = [0.1, 0.2, 0.3, 0.4];

counter = 1;
for p ∈ parameter_value_array
    
    # utility function -
    my_utility_model = build(VLLinearUtilityFunction, (
        α = [p],
    ));

    # evaluate the utility function -
    utility_array = evaluate(my_utility_model, goods_array);

    # plot -
    plot!(goods_array, utility_array, label="α = $(p)", lw=4, c=colors[counter],
        bg=:snow2, background_color_outside="white", framestyle = :box, fg_legend = :transparent);

    global counter += 1;
end
current()
xlabel!("Good or Service 1 (units)", fontsize=18);
ylabel!("Utility (utils)", fontsize=18);
```


(content:references:rational-choice-theory-utility-functions-log)=
#### Logarithmic utility functions
A logarithmic utility function assumes that an individual's utility is a function of the logarithm of the quantity consumed:

```{math}
:label: eq-log-utility
U(x) = \ln(\alpha^{T}\cdot{x}+\beta)
```

where $\beta>0$ is a positive constant, and $\alpha^{T}\cdot{x}$ is the scalar product of the vector of parameters $\alpha$ and the vector of goods or services $x$, where $x_{i}>0$ and $\alpha_{i}>0$. Let's consider four agents with incresing values of $\alpha$ but with the same value of $\beta$ ({numref}`fig-log-utility-1d`).

 ```{figure} ./figs/Fig-Log-Utility-Schematic.png
---
height: 380px
name: fig-log-utility-1d
---
Log utility function in one dimension as a function of the quantity of good or service consumed and the values of the utility function parameter $\alpha$ with $\beta = 1.0$
```


* Despite the difference in absolute utility values among the agents, their preferences remain the same. For instance, Agent 2 strictly prefers $B\succ{A}$. 
* Unlike the linear utility function, the logarithmic utility function exhibits [diminishing marginal utility](https://www.investopedia.com/terms/l/lawofdiminishingutility.asp), i.e., as a person consumes more of a good, the additional satisfaction gained from each unit consumed decreases. 

##### Implementation
We used the [VLDecisionsPackage.jl](https://github.com/varnerlab/VLDecisionsPackage.jl) to build a `log` utility function model, an instance of the `VLLogUtilityFunction` type,  and compute the utility values using the `evaluate(...)` function.  We plot the utility function using the [Plots.jl](https://github.com/JuliaPlots/Plots.jl) package. The code that produced {numref}`fig-log-utility-1d` is shown below:

```{code-block} julia
:caption: Log utility function model in Julia
:linenos:

# load packages -
using VLDecisionsPackage
using Plots
using Colors

# setup colors -
colors = Dict{Int,RGB}()
colors[1] = parse(Colorant, "#D81B60")
colors[2] = parse(Colorant, "#1E88E5")
colors[3] = parse(Colorant, "#FFC107")
colors[4] = parse(Colorant, "#004D40")

# setup ranges and parameters -
goods_array = range(0.0,stop=100.0,step=1.0) |> collect;
parameter_value_array = [0.1, 0.2, 0.3, 0.4];

# main loop -
counter = 1;
for p ∈ parameter_value_array
    
    # build a utility function model -
    my_utility_model = build(VLLogUtilityFunction, (
        α = [p], β = 1.0
    ));

    # evaluate the utility function model for the goods array -
    utility_array = evaluate(my_utility_model, goods_array);

    # plot -
    plot!(goods_array, utility_array, label="α = $(p)", lw=4, c=colors[counter],
        bg=:snow2, background_color_outside="white", framestyle = :box, 
        fg_legend = :transparent);

    global counter += 1;
end
current()
xlabel!("Good or Service 1 (units)", fontsize=18);
ylabel!("Utility (utils)", fontsize=18);
```

(content:references:rational-choice-theory-utility-functions-cobb-douglas)=
#### Cobb-Douglas utility functions
The Cobb-Douglas utility function governs the consumption of multiple goods or services and is given by:

```{math}
:label: eq-cobb-douglas-utility
U(x_{1},\dots,x_{n}) = \prod_{i\in{1\dots{n}}}{x_{i}^{\alpha_{i}}}
```

where the exponents sum to unity $\sum_{i\in{1\dots{n}}}\alpha_{i} = 1$, and $\alpha_{i}\geq{0}$. 

 ```{figure} ./figs/Fig-CobbDouglas-Utility-Schematic.png
---
height: 380px
name: fig-cobbdouglas-utility-1d
---
Cobb utility function in one dimension as a function of the quantity of good or service consumed and the values of the utility function parameters $\alpha$. We assumed $x_{2} = 1.0$ for all values of $x_{1}$, and $\sum\alpha = 1$.
```

* Different agents have varying utility values when consuming 75 units of $x$, labeled as points B, C, D, and E. Agent 4 has the highest value of $\alpha$ and obtains the highest utility value at point E, while Agent 1 has the lowest value of $\alpha$ and the lowest utility value at point B.
* Preferences differ among the agents. Agent 1 appears to weakly prefer $B\succsim{A}$, which indicates that they are nearly indifferent to consuming 75 units of $x$ versus 50 units of $x$. However, Agent 4 strictly prefers $E\succ{F}$.
* Like the log utility, the Cobb-Douglas utility function reflects [diminishing marginal utility](https://www.investopedia.com/terms/l/lawofdiminishingutility.asp), meaning that as a person consumes more of a good, the additional satisfaction gained from each unit consumed decreases.

##### Implementation
We used the `build(...)` method of [VLDecisionsPackage.jl](https://github.com/varnerlab/VLDecisionsPackage.jl) to build a `Cobb Douglas` utility function model, which is an instance of the `VLCobbDouglasUtilityFunction` type,  and then calculated the utility values using the `evaluate(...)` function.  Finally, we ploted the utility function values using the [Plots.jl](https://github.com/JuliaPlots/Plots.jl) package. The code that produced {numref}`fig-cobbdouglas-utility-1d` is shown below:

```{code-block} julia
:caption: Cobb-Douglas utility function
:linenos:

# load packages -
using VLDecisionsPackage
using Plots
using Colors

# setup colors -
colors = Dict{Int,RGB}()
colors[1] = parse(Colorant, "#D81B60")
colors[2] = parse(Colorant, "#1E88E5")
colors[3] = parse(Colorant, "#FFC107")
colors[4] = parse(Colorant, "#004D40")

# goods array -
number_of_steps = 100;
goods_array = zeros(number_of_steps,2);
for i ∈ 1:number_of_steps
    goods_array[i,1] = i |> Float64;
    goods_array[i,2] = 1.0;
end
parameter_value_array = [0.1, 0.2, 0.3, 0.4];

# main loop -
counter = 1;
for p ∈ parameter_value_array

    # utility function -
    my_utility_model = build(VLCobbDouglasUtilityFunction, (
        α = [p, 1.0-p],
    ));

    # evaluate the utility function -
    utility_array = evaluate(my_utility_model, goods_array);

    # plot -
    plot!(goods_array[:,1], utility_array, label="α = $(p)", lw=4, c=colors[counter],
        bg=:snow2, background_color_outside="white", framestyle = :box, 
        fg_legend = :transparent);

    global counter += 1;
end
current()
xlabel!("Good or Service 1 (units)", fontsize=18);
ylabel!("Utility (utils)", fontsize=18);
```

(content:references:rational-choice-theory-utility-functions-leontief)=
#### Leontief utility functions
The Leontief utility function, first developed by [Wassily Leontief](https://en.wikipedia.org/wiki/Wassily_Leontief), governs the choice between multiple states (or configurations) of the world and is given by:

```{math}
:label: eq-leontief-utility
U(x_{1},\dots, x_{n}) = \min\left\{x_{1}/\alpha_{1},\dots,x_{n}/\alpha_{n}\right\}
```

where $\alpha_{i}>{0}$ and $x_{i}\geq{0}$ for all $i\in{1\dots{n}}$. 

(content:references:marginal-utility)=
## Marginal utility
The marginal utility of a good or service is the added satisfaction or benefit that a consumer gains from consuming one more unit of a good or service ({prf:ref}`defn-marginal-utility`):

````{prf:definition} Marginal Utility
:label: defn-marginal-utility

Let $x_{i}~(\text{for}~i\in{1\dots{n}})$ be a good or service in the set of goods and services $X$. Further, let $U:X\rightarrow\mathbb{R}$ be a utility function over the set of goods $X$. Then, the [marginal utility](https://en.wikipedia.org/wiki/Marginal_utility) of $x\in{X}$ is the partial derivative of $U$ with respect to $x$:

```{math}
\bar{U}_{x_{i}} \equiv \left(\frac{\partial{U}}{\partial{x_{i}}}\right)_{\star}
```

evaluated at a point $x^{\star}\in{X}$. The change in the utility governing the decision maker can be computed using the [total differential](https://en.wikipedia.org/wiki/Differential_of_a_function#Differentials_in_several_variables) around a point $x^{\star}\in{X}$:

```{math}
:label: eqn-total-differential-ic

dU = \sum_{i\in{1\dots{n}}}\bar{U}_{x_{i}}\cdot{dx_{i}}
```

where $\bar{U}_{x_{i}}$ denotes the marginal utility of $x_{i}$ and $dx_{i}$ denotes the change in the consumption of good or service $x$.
````

This theory operates on the premise that the satisfaction or benefit from each extra unit decreases as a consumer increases the number of units consumed. The concept of Marginal Utility is crucial in shaping consumer behavior, prices, and market equilibrium.

### Why is marginal utility important?
The concept of marginal utility holds great importance for various reasons:

1. **Consumer Choice and Preferences:** Marginal utility helps explain how individuals make choices when allocating their limited resources (such as money and time) among different goods and services. Consumers typically aim to maximize their total utility, and they do this by allocating their resources in a way that equalizes the marginal utility per unit of money spent across different goods. In other words, consumers tend to purchase more of a good when its marginal utility is relatively high compared to its price.

2. **Law of Diminishing Marginal Utility:** This law states that as a person consumes more units of a good or service, the additional satisfaction (marginal utility) derived from each successive unit tends to decrease. This principle highlights why people are willing to pay more for the first few units of a good and why demand for a product decreases as consumption increases. It also explains why variety is preferred over excessive consumption of a single item.

3. **Pricing and Demand:** Businesses use the concept of marginal utility to determine the optimal pricing strategy for their products. They understand that consumers are more likely to purchase products with higher marginal utility at a given price point. By understanding how price changes affect consumers' perceived marginal utility, businesses can adjust their pricing strategies to maximize profits and meet demand.

4. **Resource Allocation:** Beyond individual consumption choices, the marginal utility helps societies allocate resources efficiently. It assists policymakers and governments in making decisions related to resource allocation, taxation, and public goods provision. By understanding how marginal utility varies across different individuals and goods, policymakers can work toward improving overall social welfare.

5. **Economic Efficiency:** The concept of marginal utility is closely related to economic efficiency. Efficient resource allocation occurs when the last unit of a good is distributed so that the marginal utility is equal across different goods. This ensures that resources are allocated to their most valued uses, leading to a more productive and prosperous economy.

6. **Consumer Surplus:** Marginal utility is used to calculate consumer surplus, which represents the difference between the total amount consumers are willing to pay for a good and the amount they pay. Consumer surplus is a measure of the net benefit consumers receive from their purchases, providing insights into the overall economic welfare of consumers.

In conclusion, the concept of marginal utility helps economists, businesses, and policymakers understand how individuals make choices and how markets function, ultimately contributing to a deeper understanding of financial systems.

### Examples: marginal utility functions
The marginal utility of a good or service for an agent that is governed by a linear utility function is constant and independent of the amount of the good or service consumed:

```{math}
\bar{U}_{x_{i}} = \alpha_{i}
```

If both a product, such as potato chips, and a consumer, like yourself, follow a linear utility function, then the additional satisfaction gained from consuming each unit is constant and not influenced by the quantity already consumed. Thus, the first chip is just as enjoyable as the last.

However, if an agent and goods are governed by a concave utility function, e.g., the [Cobb-Douglas utility function](content:references:rational-choice-theory-utility-functions-cobb-douglas) then the marginal utility of a good or service decreases as the amount of the good or service consumed increases:

```{math}
:label: eqn-mu-u-function
\bar{U}_{x_{i}} = \left(\alpha_{i}\cdot{x}^{\alpha_{i}-1}\right)\cdot\left(\prod_{j=1,i}^{n}x_{j}^{\alpha_{j}}\right)
```

where the $j=1,i$ notation denotes the _exclusion_ of index $i$. As $x_{i}\rightarrow\infty$, the marginal utility $\bar{U}_{x_{i}}\rightarrow{0}$ if $\alpha_{i}<1$. To compute analytical expressions for the marginal utility, instead of remembering the [differentiation rules from calculus](https://en.wikipedia.org/wiki/Differentiation_rules), we can use one of many [Computer Algebra Systems (CAS)](https://en.wikipedia.org/wiki/Computer_algebra_system), e.g., the [Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl) package in [Julia](https://julialang.org) or the [SymPy](https://www.sympy.org/en/index.html) library in [Python](https://www.python.org).

Sample code to compute the marginal utility for the two-dimensional [Cobb-Douglas utility function](https://en.wikipedia.org/wiki/Cobb–Douglas_production_function) using the [Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl) package:

```julia
# load the Symbolics.jl package (assumed to be installed)
using Symbolics

# declare variables (symbols in the eqn)
@variables x,y,α,β

# Build differential operators for x
Dₓ = Differential(x);

# define the utility function
U = (x^α)*(y^β)

# compute the derivative -
∂Uₓ = Dₓ(U) |> expand_derivatives;

# print -
println("The value of ∂U/∂x = ",∂Uₓ)
```

##### Numerical marginal utility 
However, sometimes it may not be convenient to analytically compute the derivative, e.g., the utility function is complicated. You can always approximate the marginal utility using a [finite difference approximation](https://en.wikipedia.org/wiki/Finite_difference), or [automatic differentiation](https://en.wikipedia.org/wiki/Automatic_differentiation) approach.

Sample code for [automatic differentiation](https://en.wikipedia.org/wiki/Automatic_differentiation) of the Cobb-Douglas utility function using the [ForwardDiff.jl](https://juliadiff.org/ForwardDiff.jl/stable/) package:

```julia
# load the ForwardDiff package
using ForwardDiff

# Cobb-Douglas utility function
function U(x)

    # initialize
    α₁ = 0.5;
    α₂ = 1.0 - α₁
    
    # return
    return (x[1]^α₁)*(x[2]^α₂)
end

# Estimate the MU -
x = [20.0,7.20]; # point A 
U = ForwardDiff.gradient(U,x);
```

<!-- ### Marginal utility and the law of diminishing marginal utility
The law of diminishing marginal utility states that as a person consumes more units of a good or service, the additional satisfaction derived from each successive unit tends to decrease. However, the law of diminishing marginal utility depends upon the utility function. For example, linear utility functions do not exhibit diminishing marginal utility. -->

## Decisions
Ultimately, the goal of rational choice theory is to make decisions that maximize the utility of the decision maker.
Let the decision maker have actions $\mathcal{A}$, observations $\mathcal{O}$ and states $\mathcal{S}$. Then, the decision maker's goal is to maximize their utility subject to various constraints, i.e., rules of the world such a budget constraints, time constraints, physical constraints such as walls, etc.




---

# Summary
In this lecture, we'll developed tools to compute rational choices and explored some mathematical and philosophical properties of utility functions:

* {ref}`content:references:rational-choice-theory` is a framework that seeks to explain human behavior by assuming that individuals make rational choices based on their preferences and goals. This theory suggests that people are motivated by self-interest and will choose actions that maximize their benefits, i.e., their utility while minimizing their costs.

* {ref}`content:references:marginal-utility` describes the added satisfaction or benefit that a consumer gains from consuming one more unit of a good or service. This theory operates on the premise that as a consumer increases the number of units consumed, the satisfaction or benefit from each extra unit decreases. The concept of Marginal Utility is crucial in shaping consumer behavior, prices, and market equilibrium.