# Risk and Risk Aversion
When individuals make decisions, they often prefer options that have lower levels of uncertainty or potential loss. This preference for minimizing potential risks over maximizing potential gains is known as risk aversion in decision-making. This cognitive bias can have an impact on a range of decisions, including investment choices, career decisions, and even personal choices related to health and safety.

```{topic} Outline

This week we discuss risk, risk aversion, and its role in decisions:

* {ref}`content:references:risk-aversion` is important for understanding how people choose between safe and risky options. This knowledge can help decision-makers develop strategies that match people’s risk preferences.

* The {ref}`content:references:measuring-risk-aversion` helps us quantify risk and its role in decision-making. The model provides insights into how people weigh potential gains and losses in uncertain situations, and aid in developing strategies that align with individuals’ risk preferences.

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

Let's develop a code to simulate this game, and use it to answer some questions. We model the coin flip as a [Bernoulli random variable](https://en.wikipedia.org/wiki/Bernoulli_distribution) with $p = 0.50$ (fair coin), and assume we have $M$ players, each performing $N$ flips:

```julia
"""
    simulate(w::Float64; N::Int64 = 100, M::Int64 = 100) -> Array{Float64,2}
"""
function simulate(w::Float64; N::Int64 = 100, M::Int64 = 100)::Array{Float64,2}

    # initialize -
    data = Array{Float64,2}(undef, M, N); # holds the simulation results
    fill!(data,0.0); # fill up the data array w/0.0 -

    # build a Bernoulli distribution, and sample it
    p = 0.5;
    flips = rand(Bernoulli(p), M, N)

    # simulation loop -
    for i ∈ 1:M # we have M players
        for j ∈ 2:N # each player does N flips -
            
            # grab a flip for player i and trial j -
            flip = flips[i,j];

            if (flip == 1) # heads
                data[i,j] = w + data[i,j-1]  # add w to current balance
            else
                data[i,j] = data[i,j-1] - w; # substract w from current balance
            end
        end
    end

    # return -
    return data
end
```

We can use the `simulate` function to calculate the experimental outcome for different values of the wealth $w$ bet on each flip and the expected return ({numref}`fig-coin-flip-simulation`):


 ```{figure} ./figs/Fig-CoinFlip-Game-Simulation.pdf
---
height: 260px
name: fig-coin-flip-simulation
---
Simulation of the cumulative cash position of $M$ players following $N$ flips of a fair coin for $w = 1$ (left) and $w = 10$ (right). Regardless of the amount bet on each flip, the expected value computed over the population of players is near zero.
```

The expected value of the coin flip game is zero for $M$ trials with $N$ flips per trial for $w = 1$ and $w = 10$; this result would be true even as $w\rightarrow\infty$. Thus, why do people react differently to betting a small versus a large amount on each coin flip if they will always break even eventually? This is the essence of an interesting characteristic of individuals, namely, risk aversion.

### Modes of Risk Aversion
Picture yourself having to choose between two options: a definite amount of money, known as the certainty equivalent (CE), or a risky payout that relies on the outcome of a coin flip, such as $100 or nothing. People’s varying attitudes towards risk cause them to opt for one choice over the other. There are three risk models that a decision-maker can adopt: risk-averse, risk-neutral, and risk-seeking ({numref}`fig-risk-aversion-types`): 

 ```{figure} ./figs/Fig-RiskAversion-Types.pdf
---
height: 240px
name: fig-risk-aversion-types
---
Utility versus wealth $W$ for three models of risk; risk-avoiding (left), risk-neutral (center), and risk-seeking (right). CE: certainty equivalent and $\mathbb{E}(W)$ expected wealth.
```

Assuming a fair coin, the expected value of the game proposed is $\mathbb{E}(W)$ = 50 USD. However, people may have different reactions when given the option of taking the bet or a certain payment:

* __Risk-averse__ individuals would prefer a certainty equivalent of less than 50 USD (for instance, 10 USD) instead of taking the gamble and possibly ending up with nothing. This means that $\text{CE} < \mathbb{E}(W)$ for a risk-averse individual.
* __Risk-neutral__ individuals are indifferent between the bet and a certain payment of 50 USD. Therefore, $\text{CE} = \mathbb{E}(W)$.
* __Risk-seeking__ individuals would take the bet even when the guaranteed payment is greater than 50 USD. This implies that $\text{CE} > \mathbb{E}(W)$. In other words, a risk-seeking individual is willing to pay to accept uncertainty.

The difference between the certainty equivalent and the expected payout of the game $\mathbb{E}(W)$ is referred to as the _risk premium_ or $\text{RP}$:

```{math}
:label: eqn-risk-premimum
\text{RP} = \mathbb{E}(W) - \text{CE}
```

For risk-averse individuals, the risk premium is positive. For risk-neutral decision-makers, the risk premium is zero. However, for risk-seeking individuals, the risk premium is negative. This means that the decision maker is willing to pay to take a chance.

(content:references:measuring-risk-aversion)=
## Arrow-Pratt model of Risk Aversion
The [Arrow-Pratt risk aversion model](https://en.wikipedia.org/wiki/Risk_aversion) is a widely used framework in economics and decision theory for measuring and analyzing individuals' risk preferences {cite}`Hanson-1970`. Proposed by economists [Kenneth Arrow](https://en.wikipedia.org/wiki/Kenneth_Arrow) and [John W. Pratt](https://en.wikipedia.org/wiki/John_W._Pratt), this model quantifies the degree of risk aversion by examining how individuals' utility functions respond to changes in wealth and uncertainty {cite}`Pratt-1964`. 

The Arrow-Pratt model measures absolute and relative risk aversion, which allows decision-makers to assess the sensitivity of individuals to risk, informing optimal decision-making strategies in various domains, such as finance, insurance, and investment ({prf:ref}`defn-arrow-pratt-model`):

````{prf:definition} Arrow-Pratt model
:label: defn-arrow-pratt-model

Let $U(w)$ be a utility function describing an individuals satisfaction gained from a unit of wealth $w$. Further, let $U(w)$ be at least twice differentiable with respect to the wealth $w$. Then, the absolute risk aversion $r(w)$ is defined as:

```{math}
:label: eqn-abs-risk-aversion-model
r(w) = - \frac{U^{\prime\prime}(w)}{U^{\prime}(w)}
```

and the relative risk aversion $\bar{r}(w)$ is defined as:

```{math}
:label: eqn-relative-risk-aversion-model
\bar{r}(w) = - w\cdot\frac{U^{\prime\prime}(w)}{U^{\prime}(w)} = w\cdot{r(w)}
```

where $U^{\prime}(w)$ and $U^{\prime\prime}(w)$ denote the first and second derivative of the utility function with respect to the weath. 
````

* For a __risk avoiding__ individual, the absolute risk aversion $r(w)>0~\forall{w}$, because the utility function $U(w)$ is concave, meaning that first detivative $U^{\prime}(w)>0$ but the second derivative $U^{\prime\prime}(w)<0$. 

* For a __risk neutral__ individual, the absolute risk aversion $r(w)=0~\forall{w}$, because the utility function $U(w)$ is linear, meaning that first detivative $U^{\prime}(w) = \text{slope}$, but the second derivative $U^{\prime\prime}(w)=0$.

* For a __risk seeking__ individual, the absolute risk aversion $r(w)<0~\forall{w}$, because the utility function $U(w)$ is convex, meaning that first detivative $U^{\prime}(w)>0$ and the second derivative $U^{\prime\prime}(w)>0$.

<!-- and the relative risk aversion $\bar{r}(w)$ is increasing in wealth $w$. For a __risk neutral__ individual, the absolute risk aversion $r(w)$ is zero, and the relative risk aversion $\bar{r}(w)$ is constant in wealth $w$. For a __risk seeking__ individual, the absolute risk aversion $r(w)$ is negative, and the relative risk aversion $\bar{r}(w)$ is increasing in wealth $w$. -->


### Example: Computing risk aversion parameters
Let's compute the absolute and relative risk aversion parameters for a typical _risk adverse_ utility function using the [FowardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl) package. For example, consider the utility function $U(w) = \log(w+1)$, which is a concave utility function. The absolute risk aversion for $U(w) = \log(w+1)$ is given by:

```{math}
:label: eqn-abs-risk-aversion-example
r(w) = \frac{1}{w+1}
```

while the releative risk aversion is given by:

```{math}
:label: eqn-relative-risk-aversion-example
\bar{r}(w) = \frac{w}{w+1}
```

A quick investigation of the above equations reveals that the absolute risk aversion is decreasing in wealth $w$, while the relative risk aversion is increasing in wealth $w$, i.e., $\lim r(w) = 0$ and $\lim \bar{r}(w) = 1$ as ${w\rightarrow\infty}$.

#### Implementation
The code block below will compute the utility function and its first and second derivatives and then compute the absolute and relative risk aversion parameters for wealth values ranging from 1 to 100:

```julia
# include packages -
using ForwardDiff

# define the utility function U(w), and its derivative U'(w) -
U(w) = log(w+1)

# setup the wealth range -
wealth_array = 1.0:1.0:100.0 |> collect;
number_of_points = length(wealth_array);

# main: compute the utility, and risk aversion for each wealth value -
risk_aversion_array = Array{Float64,2}(undef, number_of_points, 4);
for i ∈ 1:number_of_points
    
    # grab the wealth from the wealth array -
    w = wealth_array[i];

    # compute the risk aversion -
    D1 = ForwardDiff.derivative(U, w);
    D2 = ForwardDiff.derivative(x -> ForwardDiff.derivative(U, x), w)

    # store data -
    risk_aversion_array[i,1] = w;           # 1 wealth
    risk_aversion_array[i,2] = U(w);        # 2 utility
    risk_aversion_array[i,3] = -(D2/D1);    # 3 risk aversion (absolute))
    risk_aversion_array[i,4] = -w*(D2/D1);  # 4 risk aversion (relative)
end
```

A higher absolute risk aversion coefficient indicates greater aversion to risk, implying that individuals are less willing to take on additional risk for potential gains. On the other hand, the relative risk aversion coefficient is a measure of the risk aversion that is independent of the scale of wealth. 


 ```{figure} ./figs/Fig-Abs-RiskAversion-Schematic.pdf
---
height: 280px
name: fig-abs-risk-aversion
---
Utility and risk aversion versus wealth for the utility function $U(w) = \ln\left(w+1\right)$. Left: Utility versus wealth $w$. Right: Absolute risk aversion versus wealth $w$.
```

## Risk aversion and it's relationship with decisions
Risk averison is the tendency of individuals or organizations to prefer a particular outcome over an uncertain one, even if the uncertain outcome has a potentially higher expected value. Understanding risk and risk aversion is crucial for making informed decisions that involve uncertainty and can help individuals and organizations manage and mitigate potential losses.

---

## Summary
This week we discussed risk, risk aversion, and its role in decisions:

* {ref}`content:references:risk-aversion` is important for understanding how people choose between safe and risky options. This knowledge can help decision-makers develop strategies that match people’s risk preferences.

* {ref}`content:references:measuring-risk-aversion` helps us understand risk and decision-making. The model provides insights into how people weigh potential gains and losses in uncertain situations, and aid in developing strategies that align with individuals’ risk preferences.