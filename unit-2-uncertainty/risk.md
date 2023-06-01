# Risk and Risk Aversion
Risk aversion in decision making refers to the tendency of individuals to prefer options with lower levels of uncertainty or potential loss. When faced with choices, risk-averse individuals prioritize minimizing potential risks over maximizing potential gains. This cognitive bias can influence various aspects of decision making, such as investment choices, career decisions, and even personal choices involving health and safety.

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
Imagine being presented with two options: a guaranteed payoff of some amount, which we'll called the certainty equivalent (CE), or a risky payout that depends on the flip of a fair coin, e.g., either $100 or nothing. People have different attitudes towards risk, leading them to choose one option over the other. In particular, there are three models of risk that a decision-maker can be exhibit, risk-avoiding, risk-neutral, and risk-seeking ({numref}`fig-risk-aversion-types`): 

 ```{figure} ./figs/Fig-RiskAversion-Types.pdf
---
height: 240px
name: fig-risk-aversion-types
---
Utility versus wealth $W$ for three models of risk; risk-avoiding (left), risk-neutral (center), and risk-seeking (right). CE: certainty equivalent and $\mathbb{E}(W)$ expected wealth.
```

The expected value of the proposed game is $\mathbb{E}(W)$ = 50 USD. However, individuals will react differently to the choice between taking the bet or taking a certain payment:

*  __Risk avoiding__ individuals would accept a certainty equivalent of less than 50 USD (for example, 10 USD) rather than taking the gamble and possibly receiving nothing, i.e., $\text{CE} < \mathbb{E}(W)$.
* __Risk neutral__ individuals are indifferent between the bet and a certain 50 USD payment, i.e., $\text{CE} = \mathbb{E}(W)$.
* __Risk seeking__ individuals would accept the bet even when the guaranteed payment is greater than 50 USD, i.e., $\text{CE} > \mathbb{E}(W)$. In other words, a risk-seeking individual will _pay_ to accept uncertainty.

The difference between the certainty equivalent and the expected payout of the game $\mathbb{E}(W)$ is the _risk premium_ or $\text{RP}$:

```{math}
:label: eqn-risk-premimum
\text{RP} = \mathbb{E}(W) - \text{CE}
```

For risk avoiding individuals, the risk premium is positive. For risk neutral decision makers, the risk premium is zero. However, for risk seeking individuals, the risk premium is negative, i.e., the decision maker is willing to pay to take a chance.

(content:references:measuring-risk-aversion)=
## Arrow-Pratt model
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
\bar{r}(w) = - w\cdot\frac{U^{\prime\prime}(w)}{U^{\prime}(w)}
```

where $U^{\prime}(w)$ and $U^{\prime\prime}(w)$ denote the first and second derivative of the utility function with respect to the weath. 
````

Let's compute the absolute and relative risk aversion parameters for some typical utility functions using the [Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl) package.




---

## Summary
This week we discussed risk, risk aversion, and its role in decisions:

* {ref}`content:references:risk-aversion` is important for understanding how people choose between safe and risky options. This knowledge can help decision-makers develop strategies that match people’s risk preferences.

* {ref}`content:references:measuring-risk-aversion` helps us understand risk and decision-making. The model provides insights into how people weigh potential gains and losses in uncertain situations, and aid in developing strategies that align with individuals’ risk preferences.