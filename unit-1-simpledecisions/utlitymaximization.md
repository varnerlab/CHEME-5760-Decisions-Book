---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Julia
  language: julia
  name: julia-1.9
---

# Maximizing Utility
Utility maximization is the process of choosing the option that provides the highest level of utility, given a set of available options and the individual's preferences. It involves evaluating each option using a utility function and selecting the one that maximizes the utility subject to constraints.

```{topic} Outline

* {ref}`content:references:rational-choice-theory-opt` are based on the assumption that individuals have clear preferences ranked by a utility function and can evaluate the costs and benefits associated with each choice. Optimal rational choices involve selecting the option that maximizes the utility, i.e., the satisfaction derived from the decision, while considering constraints such as budgets.

* {ref}`content:references:rational-choice-income-and-prices`. Understanding the impact of income and prices on decision-making is crucial in comprehending the rationale behind the actions taken by decision makers. By studying the correlation between income, prices, and utility maximization within a budget constraint, we can gain valuable insights into consumer behavior, resource allocation, and market dynamics.

```

---


(content:references:rational-choice-theory-opt)=
## Optimal rational choices
An optimal rational decision-making agent _maximizes_ its utility function, i.e., the agent searches for a combination of goods and services that gives the highest satisfaction subject to various constraints, e.g., a budget constraint ({prf:ref}`eqn-budget-constraint`):

````{prf:definition} Maximum utility and budget constraints
:label: eqn-budget-constraint

A decision making agent has a utility function $U\left(x_{1},\dots,x_{n}\right)$ and $I$ dollars to spend between $t\rightarrow{t+dt}$. An optimal agent maximizes its utility subject to its budget:

```{math}
:label: eqn-max-ulity-problem

\begin{eqnarray}
\text{maximize}~\mathcal{O} &=& U\left(x_{1},\dots,x_{n}\right) \\
\text{subject to}~\sum_{i=1}^{n}c_{i}x_{i} & = & I\\
\text{and}~x_{i}&\geq&{0}\qquad{i=1,2,\dots,n}
\end{eqnarray}

```

where $c_{i}\geq{0}~\forall{i}$ denotes the cost of good or service $i$, and $x_{i}$ represents the amount of good or service purchased or consumed by the agent during time period $t\rightarrow{t+dt}$.

````

The problem in {prf:ref}`eqn-budget-constraint` can be solved for the unknown consumption levels of $x_{i}$ using various techniques. 

<!-- Of course, if the utility function in {prf:ref}`eqn-budget-constraint` is linear, we could also use [linear programming](https://en.wikipedia.org/wiki/Linear_programming). -->

(content:references:rational-choice-budget-constraints)=
### Budget constraints
Effective budget management involves prioritizing expenditures, making trade-offs, and seeking optimal ways to utilize the available funds within the defined buedget constraints. Budget constraints refer to the limitations imposed on an individual, organization, or government’s spending activities. These constraints arise from the finite availability of financial resources, requiring careful planning and allocation to meet various needs and goals ({prf:ref}`defn-budget-constraint`): 

````{prf:definition} Budget constraint
:label: defn-budget-constraint

Let $I$ denote the income allocated to purchase goods in a set of goods $x\in\mathcal{X}$ where $c_{x}\geq{0}$ denotes the unit cost of item $x$. Then, the budget constraint for $\mathcal{X}$ is given by:

```{math}
:label: eqn-budget-constraint
\sum_{x\in\mathcal{X}}c_{x}\cdot\dim(x) = {I}
```

The quantity $\dim(x)$ denotes the number of good $x$ purchased. The number of iterms purchased must be non-negative, i.e., $\dim(x)\geq{0}$.

````

#### Two good budget constraint: Apples and oranges
To better understand {prf:ref}`defn-budget-constraint`, let's consider the case when we have only two goods in the set of goods $\mathcal{X}$, i.e., $\mathcal{X}=\left\{\text{apples},\text{oranges}\right\}$. In this case, the budget constraint becomes a line in the $\text{apples}$ versus $\text{oranges}$ plane ({numref}`fig-two-dim-bc`).

 ```{figure} ./figs/Fig-TwoDim-BudgetConstraint-Schematic.pdf
---
height: 420px
name: fig-two-dim-bc
---
Two-dimensional budget constraint for the $\mathcal{X}=\left\{\text{apples},\text{oranges}\right\}$ set of goods.
```

The intercepts of the budget constraint shown in {numref}`fig-two-dim-bc` give the maximum amount of a good or service that can be consumed. For example, the x-intercept of the budget constraint in gives the maximum number of apples that can be purchased given the budget constraint and the price of the apple. Similarly, the y-intercept gives the maximum number of oranges that can be purchased given the budget constraint and the price of oranges.

Every point on the budget constraint line shown in {numref}`fig-two-dim-bc` indicates a possible combination of apples and oranges that could be bought within the given budget. The task at hand is to determine the optimal combination of apples and oranges that maximizes the utility function. 

### Lagrange multipliers and utility maximization
Let's begin with a classical approach, the [method of Lagrange multipliers](https://en.wikipedia.org/wiki/Lagrange_multiplier). as it provides a good foundation for understanding more advanced methods and has some interesting theoretical properties. The [method of Lagrange multipliers](https://en.wikipedia.org/wiki/Lagrange_multiplier) involves introducing additional variables, called Lagrange multipliers, which integrate the constraints into a modified objective function called the Lagrangian function ({prf:ref}`defn-method-l-multipliers`):

````{prf:definition} Method of Lagrange multipliers
:label: defn-method-l-multipliers

To find the maximum or minimum of a function $f(x)$ subject to the equality constraint $g(x)$, we can form the Lagrangian function $\mathcal{L}(x,\lambda)$:

```{math}
:label: eqn-lagrangian-1d
\mathcal{L}(x,\lambda) = f(x) + \lambda\cdot{g}(x)
```

where $\lambda$ is the Lagrange multiplier for constraint $g(x)$. At a critical point (maximum or minimum), the partial derivatives of the 
Lagrangian function with respect to $x$ and $\lambda$ vanish:

```{math}
:label: eqn-first-order-condition-lagrange

\begin{eqnarray}
\frac{\partial\mathcal{L}}{\partial{x}} & = & f^{\prime}(x) + \lambda\cdot{g^{\prime}(x)} = 0\\
\frac{\partial\mathcal{L}}{\partial{\lambda}} & = & g(x) = 0 \\
\end{eqnarray}
```

The system of equations defined by Eqn. {eq}`eqn-first-order-condition-lagrange` callled the Lagrange equations are first-order optimality conditions, which can be solved to find the critical points and, thus, the maximum or minimum value of the objective function.
````

The utility maximization problem outlined in {prf:ref}`eqn-budget-constraint` has the Lagrangian function:

```{math}
\mathcal{L}(x,\lambda) = U(x_{1},\dots,x_{n}) + \lambda\cdot\left(I-\sum_{i=1}^{n}c_{i}x_{i}\right)
```

where $I$ is the amount of money (income) we have to spend on goods $x_{1},x_{2},\dots,x_{n}$, and $c_{i}$ is the cost of good $i$. The Lagrangian function $\mathcal{L}(x,\lambda)$ can be expanded into the $n+1$ system of equations (first-order optimality conditions):

```{math}
:label: eqn-two-good-utility-maximization
\begin{eqnarray}
\frac{\partial\mathcal{L}}{\partial{x_{1}}} & = & \bar{U}_{1} - \lambda\cdot{c_{1}} = 0 \\
\vdots & = & \vdots \\
\frac{\partial\mathcal{L}}{\partial{x_{n}}} & = & \bar{U}_{n} - \lambda\cdot{c_{n}} = 0 \\
\frac{\partial\mathcal{L}}{\partial\lambda} & = & I - \sum_{i=1}^{n}c_{i}x_{i} = 0 \\
\end{eqnarray}
```

where $\bar{U}_{i}$ denotes the marginal utility of good $i$. The system of equations in Eqn. {eq}`eqn-two-good-utility-maximization` can be solved to find the optimal consumption levels of $x_{i}$. The first $n$ of the first-order optimality conditions can be solved to arrive at the following expression for the Lagrange multiplier:

```{math}
:label: eqn-lagrange-multiplier-marginal-utility-dollar
\lambda = \frac{\bar{U}_{i}}{c_{i}}\qquad\forall{i}
```

which gives an interesting interpretation of the Lagrange multiplier: it is the marginal utility per dollar spent on good $i$. Further, it provides the basis for the matching condition at the optimum:

```{math}
:label: eqn-matching-condition-marginal-utility-dollar
\frac{\bar{U}_{i}}{c_{i}} = \frac{\bar{U}_{j}}{c_{j}}\qquad\forall{i,j}
```

#### Example: Two-good Cobb-Douglas utility maximization problem
Let's consider a utility maximization problem that uses a Cobb-Douglas utility function $U(x_{1},x_{2}) = x_{1}^{\alpha}x_{2}^{1-\alpha}$ that describes the satisfaction gained from consuming two goods, $x_{1}$ and $x_{2}$. The utility function is subject to a budget constraint $\sum c_{i}x_{i} = I$, where $I$ is the amount of money (income) we have to spend on goods $x_{1}$ and $x_{2}$, and $c_{i}$ is the cost of good $i$. The Lagrangian function for this problem is given by:

```{math}
:label: eqn-lagrangian-two-good-cobb-douglas-utility
\mathcal{L}(x_{1},x_{2},\lambda) = x_{1}^{\alpha}x_{2}^{1-\alpha} + \lambda\cdot\left(I-c_{1}x_{1}-c_{2}x_{2}\right)
```

which gives the first-order optimality conditions:

```{math}
:label: eqn-two-good-cobb-douglas-utility-maximization
\begin{eqnarray}
\frac{\partial\mathcal{L}}{\partial{x_{1}}} & = & \alpha\cdot{x_{1}^{\alpha-1}}x_{2}^{1-\alpha} - \lambda\cdot{c_{1}} = 0 \\
\frac{\partial\mathcal{L}}{\partial{x_{2}}} & = & (1-\alpha)\cdot{x_{1}^{\alpha}x_{2}^{-\alpha}} - \lambda\cdot{c_{2}} = 0 \\
\frac{\partial\mathcal{L}}{\partial\lambda} & = & I - c_{1}x_{1} - c_{2}x_{2} = 0 \\
\end{eqnarray}
```

The system of equations in Eqn. {eq}`eqn-two-good-cobb-douglas-utility-maximization` can be solved to find the optimal consumption levels of $x_{1}$ and $x_{2}$. However, these equations are non-linear and not easy to solve analytically. Thus, we must use numerical methods to find the optimal values of $x_{1}$ and $x_{2}$.


#### Example: Two-good linear utility maximization problem
Let's consider a two-good utility maximization problem that uses a linear utility function $U(x_{1},x_{2}) = a_{1}x_{1}+a_{2}x_{2}$ that describes the satisfaction gained from consuming two goods, $x_{1}$ and $x_{2}$. The utility function is subject to a budget constraint $\sum c_{i}x_{i} = I$, where $I$ is the amount of money (income) we have to spend on goods $x_{1}$ and $x_{2}$, and $c_{i}$ is the cost of good $i$. The Lagrangian function for this problem is given by:

```{math}
:label: eqn-lagrangian-two-good-linear-utility
\mathcal{L}(x_{1},x_{2},\lambda) = a_{1}x_{1} + a_{2}x_{2} + \lambda\cdot\left(I-c_{1}x_{1}-c_{2}x_{2}\right)
```

which gives the first-order optimality conditions:

```{math}
:label: eqn-two-good-linear-utility-maximization
\begin{eqnarray}
\frac{\partial\mathcal{L}}{\partial{x_{1}}} & = & a_{1} - \lambda\cdot{c_{1}} = 0 \\
\frac{\partial\mathcal{L}}{\partial{x_{2}}} & = & a_{2} - \lambda\cdot{c_{2}} = 0 \\
\frac{\partial\mathcal{L}}{\partial\lambda} & = & I - c_{1}x_{1} - c_{2}x_{2} = 0 \\
\end{eqnarray}
```

This system of equations can be represented as a $3\times{3}$ system of linear algebraic equations for the unknows $\theta = \left[x_{1},x_{2},\lambda\right]^{T}$:

```{math}
\begin{bmatrix}
0 & 0 & -c_{1} \\
0 & 0 & -c_{2} \\
-c_{1} & -c_{2} & 0 \\
\end{bmatrix}
\begin{bmatrix}
x_{1} \\
x_{2} \\
\lambda \\
\end{bmatrix} = 
\begin{bmatrix}
-a_{1} \\
-a_{2} \\
-I \\
\end{bmatrix}
```

or $\mathbf{A}\mathbf{\theta} = \mathbf{b}$ which theoretically can be inverted to find the solution:

```{math}
\theta = \mathbf{A}^{-1}\mathbf{b}
```

if the matrix $\mathbf{A}$ has full rank. However, in this case, the rank of matrix $\text{rank}(\mathbf{A}) = 2$, which indicates that the system of equations is underdetermined. This means that there are an infinite number of solutions to the system of equations. To find the solution, we can use the [Moore-Penrose pseudo-inverse](https://en.wikipedia.org/wiki/Moore–Penrose_inverse) of the matrix $\mathbf{A}$, which is given by:


<!-- #### Karush-Kuhn-Tucker (KKT) conditions
The [Karush-Kuhn-Tucker (KKT) conditions](https://en.wikipedia.org/wiki/Karush–Kuhn–Tucker_conditions) are necessary conditions for finding the optimal solution to an optimization problem with constraints. The conditions are as follows:

* __Stationarity condition__: The gradient of the objective function at the optimal point is orthogonal to the feasible region, taking into account the constraints.
* __Primal feasibility condition__: The optimal solution must satisfy the constraints of the optimization problem.
* __Dual feasibility condition__: The Lagrange multipliers associated with the constraints must be non-negative.
* __Complementary slackness condition__: The product of the Lagrange multipliers and the difference between the left-hand side and right-hand side of each constraint must be zero.

These conditions provide a necessary condition for optimality, which means that if a solution satisfies these conditions, it may be a candidate for the optimal solution. However, it is not guaranteed that the optimal solution satisfies all these conditions, and additional analysis may be necessary to confirm the optimality of a candidate solution. -->

### Numerical solutions of utility maximization problems
The Cobb-Douglas utility function example above illustrates a case where the first-order optimality conditions are non-linear and not easy to solve analytically. In these cases, which are common, we must use numerical methods to find the optimal values for $x_{1},\dots,x_{n}$. 

We'll make use of the [JuMP](https://jump.dev/JuMP.jl/stable/) and [MadNLP](https://github.com/MadNLP/MadNLP.jl) packages which provide numerical techniques for solving optimization problems:
* The [JuMP](https://jump.dev/JuMP.jl/stable/) package provides a high-level interface for defining optimization problems.
* The [MadNLP](https://github.com/MadNLP/MadNLP.jl) package is used by JuMP to solve optimization problems, but it can also be used directly to solve constrained optimization problems.

Let's revisit the Cobb-Douglas utility maximization problem from above, but this time we'll use [JuMP](https://jump.dev/JuMP.jl/stable/) and [MadNLP](https://github.com/MadNLP/MadNLP.jl) to solve the problem numerically. First, we'll define a type that represents the problem (and stores useful data about the problem):

```julia
mutable struct MySimpleCobbDouglasChoiceProblem <: AbstractSimpleChoiceProblem

    # data -
    α::Array{Float64,1}
    c::Array{Float64,1}
    I::Float64
    bounds::Array{Float64,2}
    initial::Array{Float64,1}

    # constructor
    MySimpleCobbDouglasChoiceProblem() = new();
end
```

Next, we'll define a function that takes an instance of the `MySimpleCobbDouglasChoiceProblem` problem object, solves the constrained utility maximization problem, and returns a [dictionary](https://docs.julialang.org/en/v1/base/collections/#Dictionaries) with the results:


```julia
"""
    solve(problem::MySimpleCobbDouglasChoiceProblem) -> Dict{String,Any}

Solves the optimal decision problem with a budget constraint with a Cobb-Douglas utility function
"""
function solve(problem::MySimpleCobbDouglasChoiceProblem)::Dict{String,Any}

    # initialize -
    results = Dict{String,Any}()
    α = problem.α;
    c = problem.c;
    bounds = problem.bounds;
    I = problem.I;
    xₒ = problem.initial

    # how many variables do we have?
    d = length(α);

    # Setup the problem -
    model = Model(()->MadNLP.Optimizer(print_level=MadNLP.INFO, max_iter=500))
    @variable(model, bounds[i,1] <= x[i=1:d] <= bounds[i,2], start=xₒ[i]) # we have d variables
    
    # set objective function -   
    @NLobjective(model, Max, (x[1]^α[1])*(x[2]^α[2]));
    @constraints(model, 
        begin
            # my budget constraint
            transpose(c)*x <= I
        end
    );

    # run the optimization -
    optimize!(model)

    # populate -
    x_opt = value.(x);
    results["argmax"] = x_opt
    results["budget"] = transpose(c)*x_opt; 
    results["objective_value"] = objective_value(model);

    # return -
    return results
end
```

Finally, we'll put it all together and solve the problem. We build the problem object using the `build(...)` function, and then call the `solve(...)` function to estimate the optimal solution:

```{code-block} julia
:caption: runme-cobb-douglas.jl
:linenos:

# include the include (load the reqd packages) -
include("Include.jl")

# initialize -
α = [0.55, 0.45]; # coefficients
c = [2.0, 4.0]; # price of x1 and x2

# build my problem object -
problem = build(MySimpleCobbDouglasChoiceProblem, (
    
    initial = 0.1*ones(2), # initial guess
    α = α, # coefficients
    c = c, # price of x1 and x2
    I = 100.0, # income
    
    # how much of x₁ and x₂ can be we buy?
    bounds = [
        0.0 100.0; # L U
        0.0 100.0; # L U
    ]
));

# call tghe solve function. This will return a dictionary -
solution = solve(problem);
```

The optimal solution for the consumption of good $x_{1}$ and $x_{2}$ subject to the budget constraint is a point of tangency between the indifference curve and the budget constraint ({numref}`fig-two-dim-bc-cd-soln`):

 ```{figure} ./figs/Fig-Single-Budget-CD-Soln.pdf
---
height: 420px
name: fig-two-dim-bc-cd-soln
---
Optimal solution for the two-dimensional goods problem assuming a Cobb-Douglas utility function. Parameters: $\alpha_{1} = 0.55$, $\alpha_{2} = 0.45$, $c_{1} = 2$, $c_{2} = 4$, and $I = 100$. The optimal combination: $x_{1}^{*} = 27.5$, $x_{2}^{*} = 11.25$.
```

Let's check the first-order optimality conditions to make sure the solution is optimal:

```{code-cell} julia
# specify parameters (and solution) from the problem
α, c₁, c₂, x₁, x₂, I = 0.55, 2.0, 4.0, 27.5, 11.25, 100.0

# compute the marginal utility at the optimum -
Ū₁ = α*(x₁^(α-1))*(x₂^(1-α))
Ū₂ = (1-α)*(x₁^(α))*(x₂^(-α))

# compute the Lagrange multiplier -
λ = Ū₁/c₁;

# Compute the first-order conditions -
E1 = Ū₁ - λ*c₁
E2 = Ū₂ - λ*c₂
E3 = I - (c₁*x₁ + c₂*x₂)

# print -
println("Optimality conditions: $(E1), $(E2), $(E3) with λ = $(λ)")
```


(content:references:rational-choice-income-and-prices)=
## The role of income and prices
By examining the relationship between income, prices, and utility maximization subject to a budget constraint, we gain valuable insights into consumer behavior, resource allocation, and market dynamics.


---

# Summary
In this set of lectures, we discussed optimal rational choices and constrained utility maximization. We learned how to solve constrained utility maximization problems using the Lagrangian method and numerical optimization. We also explored how the optimal solution changes as a function of available income and the prices of goods and services.

* {ref}`content:references:rational-choice-theory-opt` are based on the assumption that individuals have clear preferences ranked by a utility function and can evaluate the costs and benefits associated with each choice. Optimal rational choices involve selecting the option that maximizes the utility, i.e., the satisfaction derived from the decision, while considering constraints such as budgets.

* {ref}`content:references:rational-choice-income-and-prices`. Understanding the impact of income and prices on decision-making is crucial in comprehending the rationale behind the actions taken by decision-makers. By studying the correlation between income, prices, and utility maximization within a budget constraint, we can gain valuable insights into consumer behavior, resource allocation, and market dynamics.