(content:references:utility-functions-and-choices)=
# Utility Functions and Choices

```{topic} Outline
This week, we'll introduce utility functions, and explore some mathematical and philosophical properties of utility functions:

* {ref}`content:references:rational-choice-theory` is a framework that seeks to explain human behavior by assuming that individuals make rational choices based on their preferences and goals. This theory suggests that people are motivated by self-interest and will choose actions that maximize their benefits, i.e., their utility while minimizing their costs.

* {ref}`content:references:marginal-utility` describes the added satisfaction or benefits that a consumer gains from consuming one more unit of a good or service. This theory operates on the premise that the happiness or benefit from each extra unit decreases as a consumer increases the number of units consumed. Marginal utility is crucial in shaping consumer behavior, prices, and market equilibrium.

* [Discrete choice theory](content:references:discrete-choice-experiments) is a framework for modeling choices made by individuals from a set of discrete alternatives. It is used to model the behavior of agents who have to choose among a finite set of alternatives. The theory is used in many fields, including economics, marketing, transportation planning, and environmental science.

```



---

## Introduction
Utility functions are mathematical expressions that indicate an individual’s preferences for different choices, outcomes, or states of the word. They give a numerical value, known as `utility`, for each available option, outcome, or state of the world. The `utility` can be considered a proxy for happiness or satisfaction. Thus, a larger utility is always better than a smaller utility. 

Utility functions are used in economics to model preferences and choices and predict consumer behavior. They are also used in decision theory, game theory, and other fields that study human behavior. Thus, utility functions are vital to the theory of choice, as they can be used by individuals to assign numerical values to different available options ({prf:ref}`defn-individual-utility`):

````{prf:definition} Ordinal utility function
:label: defn-individual-utility

An individual decision-maker (agent) is given a set of $n$ objects or features,  $X=\left\{x_{1} \dotsc ,x_{n}\right\}$.  A `utility function` ranks the agent's preference for combinations of these objects or features:


```{math}
:label: eqn-utility-function-generic
U(x_{1},x_{2},\dots,x_{n}) = u
```

where $u$ is a real number called the `utility` which has units of `utils`. 

* The utility function $U:X\rightarrow\mathbb{R}$ is unique only up to an order-preserving transformation. 
* Utility functions are `ordinal`, i.e., they rank-order bundles but do not measure differences between bundles
````

(content:references:rational-choice-theory)=
## Rational choice theory
[Rational choice theory](https://en.wikipedia.org/wiki/Rational_choice_theory) is founded on the idea that individuals make decisions that maximize their utility. The theory assumes that individuals always make prudent and logical decisions that provide them with the highest personal utility. In other words, when faced with competing alternatives, a decision-making agent will _always_ choose the option that maximizes their utility. 

The utility function $U:X\rightarrow\mathbb{R}$ can be used to rank order the preference for different choices. For example, suppose we have two bundles of goods, services, or states option(s) $A\in{X}$ and $B\in{X}$ that we must decide between:

* If the decision maker _strictly prefers_  option $A$ over $B$, denoted as $A\succ{B}$, the utility $U(A)$ is always greater than $U(B)$, i.e., $U(A)>U(B)$. 
* If the decision maker is _indifferent_ between option $A$ and $B$, denoted as $A\sim{B}$, then the utility $U(A)=U(B)$. 
* If the decision maker _weakly prefers or is indifferent_ between option $A$ over $B$, denoted as $A\succsim{B}$, then the utility $U(A)\geq{U(B)}$.

```{admonition} Key Idea of Rational Choice Theory
When faced with competing alternatives, i.e., different options $A$ and $B$, a rational decision maker will _always_ choose the option that maximizes their utility.
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
A  `linear` utility function assumes an individual's is directly proportional to the decision or feature variables, e.g., the quantity of a good or service consumed, the state of the world, etc. A `linear` utility function is given by:

```{math}
:label: eqn-linear-utility-function
U(x) = \alpha^{T}\cdot{x}
```

The term $\alpha^{T}\cdot{x}$ denotes the inner (or scalar) product between the $n\times{1}$ parameter vector $\alpha$ and the $n\times{1}$ vector of feature variables $x$, where $x_{i}\geq{0}$ and $\alpha_{i}>0$. Let's consider a one-dimensional linear utility function for four decision-making agents with $\alpha_{1}<\alpha_{2}<\alpha_{3}<\alpha_{4}$ where the features are the quantity of a good or service ({numref}`fig-linear-utility-1d`).

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
* A linear utility function has constant [constant marginal utility](https://en.wikipedia.org/wiki/Marginal_utility), meaning the satisfaction gained from each additional unit of $x$ remains constant.

##### Implementation
We used the [VLDecisionsPackage.jl](https://github.com/varnerlab/VLDecisionsPackage.jl) to build an instance of the `VLLinearUtilityFunction` utility function model. We then plotted the utility function using the `plot` command from the [Plots.jl](https://github.com/JuliaPlots/Plots.jl) package:

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
A `logarithmic` utility function assumes that an individual's utility is a function of the logarithm of the weighted sum of the feature variables, e.g., the quantity of a good or service consumed, the state of the world, etc., plus a constant. A `logarithmic` utility function has the form:


```{math}
:label: eq-log-utility
U(x) = \ln(\alpha^{T}\cdot{x}+\beta)
```

where $\beta>0$ is a positive constant. The term $\alpha^{T}\cdot{x}$ denotes the inner (or scalar) product between the $n\times{1}$ parameter vector $\alpha$ and the $n\times{1}$ vector of featrure variables $x$, where $x_{i}\geq{0}$ and $\alpha_{i}>0$.  The `logarithmic` utility function is the log transformation of the `linear` utility function where $\beta=0$. Let's consider four agents with incresing values of $\alpha$ but with the same value of $\beta$ ({numref}`fig-log-utility-1d`).

 ```{figure} ./figs/Fig-Log-Utility-Schematic.png
---
height: 380px
name: fig-log-utility-1d
---
Log utility function in one dimension as a function of the quantity of good or service consumed and the values of the utility function parameter $\alpha$ with $\beta = 1.0$
```

**Properties of the Logarithmic utility function**
* Despite the difference in absolute utility values among the agents, their preferences remain the same. For instance, Agent 2 strictly prefers $B\succ{A}$. 
* Unlike the linear utility function, the logarithmic utility function exhibits [diminishing marginal utility](https://www.investopedia.com/terms/l/lawofdiminishingutility.asp), i.e., as a person consumes more of a good, the additional satisfaction gained from each unit consumed decreases. 

##### Implementation
We used the [VLDecisionsPackage.jl](https://github.com/varnerlab/VLDecisionsPackage.jl) to build an instance of a `VLLogUtilityFunction` model, and computed the utility values using the `evaluate(...)` function.  We then plotted the utility function using the `plot(...)` command from the [Plots.jl](https://github.com/JuliaPlots/Plots.jl) package:

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
The `Cobb-Douglas` utility function is the product of the $n$ feature variables, thus, it models situations where the features (consumption of goods or services, traits like make, model and color of a car, etc) occur simultaneously. Each feature variable (or good, or service) is raised to a non-negative exponent:

```{math}
:label: eq-cobb-douglas-utility
U(x_{1},\dots,x_{n}) = \prod_{i\in{1\dots{n}}}{x_{i}^{\alpha_{i}}}
```

In our realization of the `Cobb-Douglas` utility, the exponents sum to unity $\sum_{i\in{1\dots{n}}}\alpha_{i} = 1$, $x_{i}\geq{0}$, and $\alpha_{i}\geq{0}$. 

 ```{figure} ./figs/Fig-CobbDouglas-Utility-Schematic.png
---
height: 380px
name: fig-cobbdouglas-utility-1d
---
Cobb-Douglas utility function in one dimension as a function of the quantity of good or service $x_{1}$ consumed and the values of the utility function parameters $\alpha$. We assumed $x_{2} = 1.0$ for all values of $x_{1}$, and $\sum\alpha = 1$.
```

**Properties of the Cobb-Douglas utility function**
* Different agents have varying utility values when consuming 75 units of $x$, labeled as points B, C, D, and E. Agent 4 has the highest value of $\alpha$ and obtains the highest utility value at point E, while Agent 1 has the lowest value of $\alpha$ and the lowest utility value at point B.
* Preferences differ among the agents. Agent 1 appears to weakly prefer $B\succsim{A}$, which indicates that they are nearly indifferent to consuming 75 units of $x$ versus 50 units of $x$. However, Agent 4 strictly prefers $E\succ{F}$.
* Like the log utility, the Cobb-Douglas utility function reflects [diminishing marginal utility](https://www.investopedia.com/terms/l/lawofdiminishingutility.asp), meaning that as a person consumes more of a good, the additional satisfaction gained from each unit consumed decreases.

##### Implementation
We used the `build(...)` method of the [VLDecisionsPackage.jl](https://github.com/varnerlab/VLDecisionsPackage.jl) package to build an instance of a `VLCobbDouglasUtilityFunction` model,  and then calculated the utility values using the `evaluate(...)` function.  Finally, we ploted the utility function values using the `plot(...)` command from the [Plots.jl](https://github.com/JuliaPlots/Plots.jl) package:

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
The `Leontief` utility function, first developed by [Wassily Leontief](https://en.wikipedia.org/wiki/Wassily_Leontief) who was later awared a [Nobel Prize in Economics for his work](https://www.nobelprize.org/prizes/economic-sciences/1973/leontief/facts/), computes the utility for `complementary` states (or configurations) of the world, where each feature variable is scaled by a non-negative constant(s) $\alpha$. The `Leontief` utility function is given by:

```{math}
:label: eq-leontief-utility
U(x_{1},\dots, x_{n}) = \min\left\{\frac{x_{1}}{\alpha_{1}},\dots,\frac{x_{n}}{\alpha_{n}}\right\}
```

where $\alpha_{i}>{0}$ and $x_{i}\geq{0}$ for all $i\in{1\dots{n}}$. For example, suppose we wanted to make a cheese sandwich. For this, we need two slices of bread and one slice of cheese where $X = \left\{\text{bread},\text{cheese}\right\}$, i.e., the number of slices of bread and pieces of cheese we have. The Leontief utility function $U(\dots)_{\text{sandwich}}$ for the sandwich is then given by:

```{math}
:label: eq-leontief-utility-sandwhich
U(x_{1},x_{2})_{\text{sandwich}} = \min\left\{\frac{x_{1}}{2},\frac{x_{2}}{1}\right\}
```

where $x_{1}$ and $x_{2}$ denote the number of slices of bread and cheese we have, respectively. Let's simulate the utility function for the sandwich using the [VLDecisionsPackage.jl](https://github.com/varnerlab/VLDecisionsPackage.jl) package.

##### Implementation
We used the `build(...)` method of the [VLDecisionsPackage.jl](https://github.com/varnerlab/VLDecisionsPackage.jl) package to build an instance of the `VLLeontiefUtilityFunction` utility model, and then calculated the utility values using the `evaluate(...)` function:

```{code-block} julia
:caption: Leontief utility function
:linenos:

# load external packages -
include("Include.jl")

# initialize -
max_number_of_bread_slices = 4;
max_number_of_cheese_slices = 4;
bread_array = range(0,max_number_of_bread_slices,step=1) |> collect;
cheese_array = range(0,max_number_of_cheese_slices,step=1) |> collect;
df = DataFrame();

# # build a utility function model -
model = build(VLLeontiefUtilityFunction, (
    α = [2.0, 1.0], # parameters: bread, cheese
));

# main -
for i ∈ eachindex(bread_array)
    
    # get the number of bread slices -
    number_of_bread_slices = bread_array[i];
    
    for j ∈ eachindex(cheese_array)

        # get the number of cheese slices -
        number_of_cheese_slices = cheese_array[j];
        
        # compute -
        value = evaluate(model, [number_of_bread_slices, number_of_cheese_slices]);

        # package -
        results_tuple = (
            bread = number_of_bread_slices,
            cheese = number_of_cheese_slices,
            U = value
        );
        push!(df, results_tuple);
    end
end
```

Using the code block above, we computed the utility function for the sandwich problem for different combinations of the number of slices of bread and cheese (Fig. {numref}`fig-leontief-utility-sandwich`).

 ```{figure} ./figs/Fig-LUF-CheeseSandwich.svg
 ---
height: 380px
name: fig-leontief-utility-sandwich
---
Leontief utility function for the cheese sandwich problem. The utility function is given by $U(x_{1},x_{2})_{\text{sandwich}} = \min\left\{\frac{x_{1}}{2},\frac{x_{2}}{1}\right\}$. The utility function is plotted as a function of the number of slices of bread and cheese.
```
 

<!-- The results of the simulation are shown in the Table:

| bread | cheese | U   |
|-------|--------|-----|
|     0 |      0 | 0.0 |
|     0 |      1 | 0.0 |
|     0 |      2 | 0.0 |
|     0 |      3 | 0.0 |
|     0 |      4 | 0.0 |
|     1 |      0 | 0.0 |
|     1 |      1 | 0.5 |
|     1 |      2 | 0.5 |
|     1 |      3 | 0.5 |
|     1 |      4 | 0.5 |
|     2 |      0 | 0.0 |
|     2 |      1 | 1.0 |
|     2 |      2 | 1.0 |
|     2 |      3 | 1.0 |
|     2 |      4 | 1.0 |
|     3 |      0 | 0.0 |
|     3 |      1 | 1.0 |
|     3 |      2 | 1.5 |
|     3 |      3 | 1.5 |
|     3 |      4 | 1.5 |
|     4 |      0 | 0.0 |
|     4 |      1 | 1.0 |
|     4 |      2 | 2.0 |
|     4 |      3 | 2.0 |
|     4 |      4 | 2.0 | -->

(content:references:marginal-utility)=
## Marginal utility
The marginal utility of a good or service is the added satisfaction or benefit that a consumer gains from consuming one more unit of a good or service ({prf:ref}`defn-marginal-utility`):

````{prf:definition} Marginal Utility
:label: defn-marginal-utility

Let $x_{i}~(\text{for}~i\in{1\dots{n}})$ be a good or service (or a state of the world) which is a member of the set $X$. Further, let $U:X\rightarrow\mathbb{R}$ be a utility function over the set $X$, i.e., the function $U$ maps a choice of goods, services or states of the world into a utility value. The [marginal utility](https://en.wikipedia.org/wiki/Marginal_utility) of $x\in{X}$ is the partial derivative of $U$ with respect to $x$:

```{math}
\bar{U}_{x_{i}} \equiv \left(\frac{\partial{U}}{\partial{x_{i}}}\right)
```

The marginal utility $\bar{U}_{x_{i}}$ measures the change in the utility $U$ resulting from small changes in $x_{i}$.
````

### Why is marginal utility important?
While the marginal utility may seem like a mathematical curiosity, it has important applications. First, the marginal utility quantifies how changing the quantity of a good or service consumed (or moving from one state of the world to another) affects the utility. In particular, the change in the utility $U(\dots)$ of the decision maker can be computed using the [total differential](https://en.wikipedia.org/wiki/Differential_of_a_function#Differentials_in_several_variables) around some starting point $x^{\star}\in{X}$:

```{math}
:label: eqn-total-differential-ic

dU = \sum_{i\in{1\dots{n}}}\bar{U}_{x_{i}}\cdot{dx_{i}}
```

where $dU\approx\left(U - U_{\star}\right)$ denotes the change in utility, $\bar{U}_{x_{i}}$ denotes the marginal utility of $x_{i}$ evaluated at the starting point, and $dx_{i}\approx(x_{i}-x_{i,\star})$ is the change in $x_{i}$. 

Equation. {eq}`eqn-total-differential-ic` is a powerful equation that we will use to derive the [marginal rate of substitution](https://en.wikipedia.org/wiki/Marginal_rate_of_substitution), which is how much of one thing we would willingly give up for another. Further, in the context of a trade between agents, Eqn. {eq}`eqn-total-differential-ic` can be used to evaluate the goodness of the trade, i.e., the change in the utility of the decision-maker experiences resulting from a trade:

 * If a trade is a `good trade` the change in utility should always be non-negative, i.e., $dU\geq{0}$.
 * If a trade is a `bad trade` the change in utility is always negative, i.e., $dU<{0}$.

Beyond these specific applications, the concept of marginal utility holds great importance for several other reasons:

1. **Consumer Choice and Preferences:** Marginal utility helps explain how individuals make choices when allocating their limited resources (such as money and time) among different goods and services. Consumers typically aim to maximize their total utility, and they do this by allocating their resources in a way that equalizes the marginal utility per unit of money spent across different goods. In other words, consumers tend to purchase more of a good when its marginal utility is relatively high compared to its price.

2. **Law of Diminishing Marginal Utility:** This law states that as a person consumes more units of a good or service, the additional satisfaction (marginal utility) derived from each successive unit tends to decrease. This principle highlights why people are willing to pay more for the first few units of a good and why demand for a product decreases as consumption increases. It also explains why variety is preferred over excessive consumption of a single item.

3. **Pricing and Demand:** Businesses use the concept of marginal utility to determine the optimal pricing strategy for their products. They understand that consumers are more likely to purchase products with higher marginal utility at a given price point. By understanding how price changes affect consumers' perceived marginal utility, businesses can adjust their pricing strategies to maximize profits and meet demand.

4. **Resource Allocation:** Beyond individual consumption choices, the marginal utility helps societies allocate resources efficiently. It assists policymakers and governments in making decisions related to resource allocation, taxation, and public goods provision. By understanding how marginal utility varies across different individuals and goods, policymakers can work toward improving overall social welfare.

5. **Economic Efficiency:** The concept of marginal utility is closely related to economic efficiency. Efficient resource allocation occurs when the last unit of a good is distributed so that the marginal utility is equal across different goods. This ensures that resources are allocated to their most valued uses, leading to a more productive and prosperous economy.

6. **Consumer Surplus:** Marginal utility is used to calculate consumer surplus, which represents the difference between the total amount consumers are willing to pay for a good and the amount they pay. Consumer surplus is a measure of the net benefit consumers receive from their purchases, providing insights into the overall economic welfare of consumers.

In conclusion, the concept of marginal utility helps economists, businesses, and policymakers understand how individuals make choices and how markets function, ultimately contributing to a deeper understanding of financial systems.

### Computing marginal utility
The marginal utility of a good or service can be computed analytically or numerically. For example, the marginal utility of a good or service for an agent that is governed by a linear utility function is constant and independent of the amount of the good or service consumed:

```{math}
\bar{U}_{x_{i}} = \alpha_{i}
```

If both a product, such as potato chips, and a consumer, like yourself, follow a linear utility function, then the additional satisfaction gained from consuming each unit is constant and not influenced by the quantity already consumed. Thus, the first chip is just as enjoyable as the last.


#### Symbolic marginal utility
Computing the marginal utility of a linear utility function is straightforward. However, most utility functions are not linear (and can be quite complex). Thus, let's use symbolic manipulation tools to compute the partial derivatives. For example, suppose an agent is using a concave utility function, e.g., the [Cobb-Douglas utility function](content:references:rational-choice-theory-utility-functions-cobb-douglas), then the marginal utility is given by:

```{math}
:label: eqn-mu-u-function
\bar{U}_{x_{i}} = \left(\alpha_{i}\cdot{x}^{\alpha_{i}-1}\right)\cdot\left(\prod_{j=1,i}^{n}x_{j}^{\alpha_{j}}\right)
```

where the $j=1,i$ notation denotes the _exclusion_ of index $i$. As $x_{i}\rightarrow\infty$, the marginal utility $\bar{U}_{x_{i}}\rightarrow{0}$ if $\alpha_{i}<1$. Thus, the satisfaction gained from comsuming an additional unit of a good or service (or moving between states in a world) decreases as the amount consumed increases.

To compute analytical expressions for the marginal utility, instead of remembering the [differentiation rules from calculus](https://en.wikipedia.org/wiki/Differentiation_rules), we can use one of many [Computer Algebra Systems (CAS)](https://en.wikipedia.org/wiki/Computer_algebra_system), e.g., the [Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl) package in [Julia](https://julialang.org) or the [SymPy](https://www.sympy.org/en/index.html) library in [Python](https://www.python.org).

Sample code to compute the marginal utility for the two-dimensional [Cobb-Douglas utility function](https://en.wikipedia.org/wiki/Cobb–Douglas_production_function) using the [Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl) package:

```{code-block} julia
:caption: Marginal utility of the Cobb-Douglas utility function
:linenos:

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

#### Numerical marginal utility 
However, sometimes it may not be convenient to analytically compute the derivative, e.g., the utility function is complicated or we need a numerical value, e.g., when evaluating the goodness of a trade. You can always approximate the value of the marginal utility using a [finite difference approximation](https://en.wikipedia.org/wiki/Finite_difference), or [automatic differentiation](https://en.wikipedia.org/wiki/Automatic_differentiation) approach.

Sample code for [automatic differentiation](https://en.wikipedia.org/wiki/Automatic_differentiation) of the Cobb-Douglas utility function using the [ForwardDiff.jl](https://juliadiff.org/ForwardDiff.jl/stable/) package:

```{code-block} julia
:caption: Numerical marginal utility of the Cobb-Douglas utility function
:linenos:

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

<!-- ## Decisions
Ultimately, the goal of rational choice theory is to make decisions that maximize the utility of the decision maker.
Let the decision maker have actions $\mathcal{A}$, observations $\mathcal{O}$ and states $\mathcal{S}$. Then, the decision maker's goal is to maximize their utility subject to various constraints, i.e., rules of the world such a budget constraints, time constraints, physical constraints such as walls, etc. -->


(content:references:discrete-choice-experiments)=
## Discrete Choice Models
Discrete choice models can be used to select between competing alternatives, such as goods, services, or states of the world, based on modeled and unmodeled factors. Developed by McFadden and coworkers in the 1970s and 1980s {cite}`MCFADDEN1973,MCFADDEN1980,BALTAS2001115`, McFadden was later awarded the [Nobel Price in Economics](https://www.nobelprize.org/prizes/economic-sciences/2000/mcfadden/facts/) for his work on discrete choice models.

Discrete choice models assume that people make decisions based on factors that are known to the decision maker, but perhaps unknown to an observer. Thus, there are observable features of the decision, and there are unobservable features that influence the decision that are not modeled. For example, suppose a person chooses one car over another based on its price, fuel efficiency, safety rating, and brand. However, the decision maker also consideres style or color as important, but these features are unobserved. Utility function of this type of decision take the form:

```{math}
:label: eqn-utility-function-dce
U_{ij} = V_{ij} + \epsilon_{ij}
```

where $U_{ij}$ is the utility of alternative $j$ for individual $i$, $V_{ij}$ is the deterministic component of the utility, i.e., the utility associated with the observable features, and $\epsilon_{ij}$ is the random component of the utility. 

```{admonition} Random utility functions (RUs)
Discrete choice utility functions incorporate randomness into the utility calculation to account for unmodeled factors that affect decision-making. This randomness arises not from the world but from our inability to capture all influencing factors.
```

### Logit choice models
The `logit` model assumes that the error terms $\epsilon_{nj}$ are independently, identically distributed (i.i.d) extreme values following a [Gumbel distribution](https://en.wikipedia.org/wiki/Gumbel_distribution). Given this assumption, and some algebraic manipulation, the probability that individual $i$ chooses alternative $j$ from a collection of $J$ choices in a `logit` model can be shown to be:

```{math}
:label: eqn-logit-probability
P_{ij} = \frac{\displaystyle \exp\left(\frac{V_{ij}}{\lambda}\right)}{\displaystyle\sum_{k\in{J}}\exp\left(\frac{V_{ik}}{\lambda}\right)}
```

where $P_{ij}$ is the probability that individual $i$ chooses alternative $j$, $V_{ij}$ is the deterministic component of the utility, i.e., the utility associated with the observable features, $J$ is the set of all alternatives and $\lambda$ is a scale parameter. The scale parameter $\lambda$ is a positive constant that controls the degree of randomness in the model. The larger the value of $\lambda$, the more random the model becomes. 

---

# Summary
In this lecture, we'll developed tools to compute rational choices and explored some mathematical and philosophical properties of utility functions:

* {ref}`content:references:rational-choice-theory` is a framework that seeks to explain human behavior by assuming that individuals make rational choices based on their preferences and goals. This theory suggests that people are motivated by self-interest and will choose actions that maximize their benefits, i.e., their utility while minimizing their costs.

* {ref}`content:references:marginal-utility` describes the added satisfaction or benefit that a consumer gains from consuming one more unit of a good or service. This theory operates on the premise that as a consumer increases the number of units consumed, the satisfaction or benefit from each extra unit decreases. The concept of Marginal Utility is crucial in shaping consumer behavior, prices, and market equilibrium.

* [Discrete choice theory](content:references:discrete-choice-experiments) is a framework for modeling choices made by individuals from a set of discrete alternatives. It is used to model the behavior of agents who have to choose among a finite set of alternatives. The theory is used in many fields, including economics, marketing, transportation planning, and environmental science.