# Maximizing Utility Subject to Constraints
Utility maximization is the process of choosing the option that provides the highest level of utility, given a set of available options and the individual's preferences. It involves evaluating each option using a utility function and selecting the one that maximizes the utility subject to constraints.

```{topic} Outline

* {ref}`content:references:rational-choice-theory-opt` is a concept in decision-making that refers to the selection of the best possible option from a set of alternatives. It is based on the assumption that individuals have clear preferences ranked by a utility function and can evaluate the costs and benefits associated with each choice. Optimal rational choices involve selecting the option that maximizes the utility, i.e., the satisfaction derived from the decision, while considering constraints such as budgets. 

* {ref}`content:references:rational-choice-budget-constraints` are a crucial factor in decision-making for individuals, businesses, and governments alike. They represent the finite resources available to make choices and allocate funds toward different options. A budget constraint forces decision-makers to weigh the costs and benefits of various options and make trade-offs based on their available resources.

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
\text{subject to}~\sum_{i=1}^{n}c_{i}x_{i} & \leq & I\\
\text{and}~x_{i}&\geq&{0}\qquad{i=1,2,\dots,n}
\end{eqnarray}

```

where $c_{i}\geq{0}~\forall{i}$ denotes the cost of good or service $i$, and $x_{i}$ represents the amount of good or service purchased or consumed by the agent during time period $t\rightarrow{t+dt}$.

````

The problem in {prf:ref}`eqn-budget-constraint` can be solved for the unknown consumption levels of $x_{i}$ using various techniques. For example, we could use the [method of Lagrange multipliers](https://en.wikipedia.org/wiki/Lagrange_multiplier) or a [penalty method](https://en.wikipedia.org/wiki/Penalty_method) in combination with any number of heuristic optimization approaches, e.g., [simulated annealing](https://en.wikipedia.org/wiki/Simulated_annealing). Of course, if the utility function in {prf:ref}`eqn-budget-constraint` is linear, we could also use [linear programming](https://en.wikipedia.org/wiki/Linear_programming).

## Solving optimal choice problems
To solve the constrained maximum utility problem, we could use classical calculus methods, i.e., the [method of Lagrange multipliers](https://en.wikipedia.org/wiki/Lagrange_multiplier) or numerical approaches such as the [method of gradient descent](https://en.wikipedia.org/wiki/Gradient_descent) or [metaheuristic approaches](https://en.wikipedia.org/wiki/Metaheuristic#Metaheuristic_Optimization_Frameworks) in combination with a [penalty](https://en.wikipedia.org/wiki/Penalty_method) or [barrier](https://en.wikipedia.org/wiki/Barrier_function) method to accommodate the constraints.

### Lagrange multipliers
The [method of Lagrange multipliers](https://en.wikipedia.org/wiki/Lagrange_multiplier) involves introducing additional variables, called Lagrange multipliers, which integrate the constraints into the objective function ({prf:ref}`defn-method-l-multipliers`):

````{prf:definition} Method of Lagrange multipliers
:label: defn-method-l-multipliers

To find the maximum or minimum of a function $f(x)$ subject to the equality constraint $g(x)$, we can form the Lagrangian function:

```{math}
:label: eqn-lagrangian-1d
\mathcal{L}(x,\lambda) = f(x) + \lambda\cdot{g}(x)
```

where $\lambda$ is the Lagrange multiplier for constraint $g(x)$, and $\mathcal{L}(x,\lambda)$ is called the Lagrangian function. At a critical point (maximum or minimum), the partial derivatives of the 
Lagrangian function with respect to $x$ and $\lambda$ vanish:

```{math}
:label: eqn-first-order-condition-lagrange

\begin{eqnarray}
\frac{\partial\mathcal{L}}{\partial{x}} & = & 0\\
\frac{\partial\mathcal{L}}{\partial{\lambda}} & = & 0\\
\end{eqnarray}
```

The system of equations defined by Eqn. {eq}`eqn-first-order-condition-lagrange` callled the Lagrange equations, can be solved to find the critical points and, thus, the maximum or minimum value of the objective function.
````

#### Karush-Kuhn-Tucker (KKT) conditions
The [Karush-Kuhn-Tucker (KKT) conditions](https://en.wikipedia.org/wiki/Karush–Kuhn–Tucker_conditions) are necessary conditions for finding the optimal solution to an optimization problem with constraints. The conditions are as follows:

* __Stationarity condition__: The gradient of the objective function at the optimal point is orthogonal to the feasible region, taking into account the constraints.
* __Primal feasibility condition__: The optimal solution must satisfy the constraints of the optimization problem.
* __Dual feasibility condition__: The Lagrange multipliers associated with the constraints must be non-negative.
* __Complementary slackness condition__: The product of the Lagrange multipliers and the difference between the left-hand side and right-hand side of each constraint must be zero.

These conditions provide a necessary condition for optimality, which means that if a solution satisfies these conditions, it may be a candidate for the optimal solution. However, it is not guaranteed that the optimal solution satisfies all these conditions, and additional analysis may be necessary to confirm the optimality of a candidate solution.

### Penalty and Barrier methods
A penalty method transforms a constrained least squares problem into an unconstrained problem that can be solved. In a penalty method, a penalty is added to the loss function to encourage specific desirable properties of the solution. 

#### Quadratic penalty functions
Before we look at the applications of penalty methods, let's consider a simple example to work out the basic strategy. This example was reproduced from the [Mathematical Optimization course at Stanford](https://web.stanford.edu/group/sisl/k12/optimization/#!index.md). Suppose we wanted to solve the problem:

```{math}
:label: eqn-example-pmethod
\begin{eqnarray}
\arg \min_{x} \left(f(x) = \frac{100}{x}\right) & &  \\
\text{subject to} & & \\
x\leq{5} & &   
\end{eqnarray}
```
Before starting, convert any constraints into the form (expression) $\leq{0}$, so the $x\leq{5}$ becomes:

```{math}
x - 5 \leq{0}
```

Once the constraints have been converted, the next step is to start charging a penalty for violating them. Since we’re trying to minimize $f(x)$, we need to _add value_ when the constraint is violated. If you are trying to maximize, the penalty will _subtract value_. With the constraint $x-5\leq{0}$ we need a penalty that is:
* __Constraint satisfied__: 0 when $x-5\leq{0}$
* __Constraint violated__: postive when $x-5>0$.

This can be done by using a penalty $P\left(x\right)$ of the form:

```{math}
:label: eqn-quad-penalty
P(x) = \max\left(0,x-5\right)^{2}
```

Eqn. {eq}`eqn-quad-penalty` is a quadratic penalty (loss) function. This approach works for equality constraints as well. For example, suppose we had the constraint $h(x) = c$, where $c$ is a constant. We can convert this type of constraint into a penalty of the form:

```{math}
:label: eqn-equality-constraint-pm
P(x) = \left(h(x) - c\right)^{2}
```

The lowest penalty value in {eq}`eqn-equality-constraint-pm` will occur when $h(x) = c$; thus, we satisfy the constraint. Once we have converted the constraints into penalty functions, we add all the penalty functions to the original objective function $f(x) + \lambda\cdot{P(x)}$ and minimize the total function (objective plus penalties). For example, the original problem in {eq}`eqn-example-pmethod` becomes:

```{math}
:label: eqn-final-penality-form
\arg \min_{x} \left(\frac{100}{x} +\lambda\cdot\max\left(0,x-5\right)^{2}\right)
```

where $\lambda$ is a _hyper-parameter_ (a parameter associated with the method, not the problem) that is adjusted during the process to estimate the unknown value of $x$ according to the policy ({prf:ref}`obs-lambda-policy`):

```{prf:observation} $\lambda$-policy penalty method
:label: obs-lambda-policy
For a penalty method, we start with a small $\lambda$ and repeat the $x$ estimation problem with larger and larger values of $\lambda$. This makes constraint violation more expensive for each subsequent refinement of the estimate of $x$.
```

With a penalty method, we can choose any value for the starting value of $x$.

#### Barrier functions
Let's rethink the problem shown in Eqn. {eq}`eqn-example-pmethod`. Suppose, instead of developing the penality function shown in Eqn. {eq}`eqn-quad-penalty` to minimize $f(x)$, for a ccontraint of the form $g(x)\leq{0}$ we developed a barrier function:

```{math}
:label: eqn-barrier-function
B\left(x\right) = - \frac{1}{g(x)}
```

As the $g(x)\rightarrow{0}$, i.e., we approach constraint violation, the value of $B\left(x\right)\rightarrow\infty$. In a similar way to penality approach shown in Eqn. {eq}`eqn-final-penality-form`, we could augment the objective (loss) function:

```{math}
:label: eqn-final-barrier-method
\arg \min_{x}\left(f(x) -\frac{1}{\lambda}\cdot{B(x)}\right)
```


The challenge of the barrier method shown in Eqn. {eq}`eqn-final-barrier-method` is selecting a starting point. The initial guess of the $x$ must be inside the barrier. If this is true, we adjust the hyperparameter $\lambda$ using the policy ({prf:ref}`obs-barrier-method-lambda-policy`):

```{prf:observation} $\lambda$-policy barrier method
:label: obs-barrier-method-lambda-policy
For a barrier method, we start with a large $\lambda$ and repeat the $x$ estimation problem with smaller and smaller values of $\lambda$. This allows us to solve the problem near the solution with limited input from the barrier. When
we gradually reduce $\lambda$, using our previous solution as a starting point, we move closer and closer to the barrier.
```

Barrier methods have on critical pathology ({prf:ref}`remark-barrier-method`):

```{prf:remark} Barrier method pathology
:label: remark-barrier-method

If, for some reason, we jump over the barrier, e.g., we start outside the feasible region (the set of $x$ values allowed by the constraints), or during the calculation, we generate a candidate solution outside the barrier, this approach can fail.
```

#### Application of penalty and barrier methods
In the context of statistical modeling, penalty, and barrier methods are often used to regularize the model, which means imposing constraints on the model parameters to prevent overfitting and improve the model’s generalization ability

Several different types of penalty methods are commonly used in statistical modeling, including:
* [Ridge regression](https://en.wikipedia.org/wiki/Ridge_regression) adds a penalty term to the loss function, which is the sum of the squares of the model parameters. This has the effect of shrinking the parameters towards zero and can help reduce the model’s variance.
* [Lasso regression](https://en.wikipedia.org/wiki/Lasso_(statistics)) adds a penalty term to the loss function, which is the sum of the absolute values of the model parameters. This has the effect of setting some of the parameters to zero, which can help to select a subset of essential features and reduce the complexity of the model.
* [Group Lasso](https://en.wikipedia.org/wiki/Lasso_(statistics)#Group_lasso) is similar to [lasso regression](https://en.wikipedia.org/wiki/Lasso_(statistics)) but allows the user to group variables together and applies the penalty to the group rather than to each variable.
* [Elastic net](https://en.wikipedia.org/wiki/Lasso_(statistics)#Elastic_net) combines the ridge and lasso regression penalties and allows users to tune the balance between the two penalties.

Penalty methods can be combined with [optimization algorithms](https://optimization.cbe.cornell.edu/index.php?title=Main_Page) to find the best (optimal) values of the model parameters that minimize the loss function subject to the penalty constraints. These methods are often used in situations with many predictors, and the goal is to select a parsimonious model with a small number of essential features.

### Heuristic optimization
Heuristic optimization is a family of algorithms inspired by natural phenomena and human behavior. Heuristic methods are often used to solve complex, real-world problems where exact solutions are difficult to obtain or may not even exist. Unlike traditional optimization methods, heuristic approaches use rules of thumb, intuition, and trial-and-error to explore the search space and find the best solution.

There are several types of heuristic optimization algorithms, including:

* [Simulated Annealing (SA)](https://en.wikipedia.org/wiki/Simulated_annealing) is inspired by the process of annealing in metallurgy. It starts with an initial solution and gradually changes it by randomly perturbing it and accepting or rejecting the new solution based on a probability function. SA is commonly used for problems that involve finding the global minimum of a non-convex function.
* [Genetic Algorithms (GA)](https://en.wikipedia.org/wiki/Genetic_algorithm) are inspired by the process of natural selection in biology. It starts with a population of potential solutions represented as chromosomes, which evolve through a series of selection, crossover, and mutation operations to create a new generation of solutions. GA is commonly used for problems that involve a large number of variables and constraints.
* [Particle Swarm Optimization (PSO)](https://en.wikipedia.org/wiki/Particle_swarm_optimization) simulates the behavior of a swarm of particles moving in a multi-dimensional search space. Each particle represents a potential solution to the problem, and it adjusts its position and velocity based on the best solution found by the swarm. PSO is commonly used for problems that require continuous optimization.
* [Ant Colony Optimization (ACO)](https://en.wikipedia.org/wiki/Ant_colony_optimization_algorithms) is inspired by the behavior of ant colonies. It involves a set of artificial ants that communicate with each other using pheromone trails to find the best path between a start and end point. ACO is commonly used for problems that find the shortest path in a graph.
* [Artificial Bee Colony (ABC)](https://en.wikipedia.org/wiki/Artificial_bee_colony_algorithm) simulates the behavior of a colony of artificial honey bees. ABC is commonly used for problems that involve finding the optimal solution in a continuous search space. Each bee represents a potential solution to the problem and adjusts its position based on the quality of the nectar source it has found.
* [Tabu Search (TS)](https://en.wikipedia.org/wiki/Tabu_search) uses a memory-based search strategy to avoid revisiting previously explored solutions. TS is commonly used for problems that involve finding the optimal solution in a combinatorial search space. It maintains a list of tabu moves, which are forbidden moves, to ensure that the search space is explored efficiently.

(content:references:rational-choice-budget-constraints)=
## Budget constraints
Fill me in

---




# Summary
Fill me in