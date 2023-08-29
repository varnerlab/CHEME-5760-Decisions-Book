# Markov Decision Processes
A Markov decision process (MDP) is an approach for modeling decision-making in situations where outcomes are partly random but also partly under the control of a _decision-maker_ who receives a reward (or penalty) for each decision.

Markov decision processes (MDPs) involve actions, which allow choice, and rewards that motivate the decision-maker.

At each time step, let's assume the system in some state $s$ in a set of possible states $s\in\mathcal{S}$ and the decision maker may choose any action $a$ from a set of possible actions $a\in\mathcal{A}$ that are available in state $s$. The system responds at the next time step by _potentially_ moving into a new state $s^{\prime}$ and rewarding the decision maker $R_{a}\left(s, s^{\prime}\right)$. The probability that the system moves into a new state $s^{\prime}$ depends upon the chosen action $a$ and the current state $s$; this probability is governed by a state transition function $P_{a}\left(s,s^{\prime}\right)$.

````{prf:definition} Markov decision tuple 
:label: defn-formal-mdp

A Markov decision process is the tuple $\left(\mathcal{S}, \mathcal{A}, R_{a}\left(s, s^{\prime}\right), T_{a}\left(s,s^{\prime}\right), \gamma\right)$ where:

* The state space $\mathcal{S}$ is the set of all possible states $s$ that a system can exist in
* The action space $\mathcal{A}$ is the set of all possible actions $a$ that are available to the agent, where $\mathcal{A}_{s} \subseteq \mathcal{A}$ is the subset of the action space $\mathcal{A}$ that is accessible from state $s$.
* An expected immediate reward $R_{a}\left(s, s^{\prime}\right)$ is received after transitioning from state $s\rightarrow{s}^{\prime}$ due to action $a$. 
* The transition $T_{a}\left(s,s^{\prime}\right) = P(s_{t+1} = s^{\prime}~|~s_{t}=s,a_{t} = a)$ denotes the probability that action $a$ in state $s$ at time $t$ will result in state $s^{\prime}$ at time $t+1$
* The quantity $\gamma$ is a _discount factor_; the discount factor is used to weight the _future expected utility_.

Finally, a policy function $\pi$ is the (potentially probabilistic) mapping from states $s\in\mathcal{S}$ to actions $a\in\mathcal{A}$ used by the agent to solve the decision task. 
````

## Policy evaluation
One immediate question that jumps out is what is a policy function $\pi$, and how do we find the best possible policy for our decision problem? To do this, we need a way to estimate how good (or bad) a particular policy is; the approach we use is called _policy evaluation_. Let's denote the expected utility gained by executing some policy $\pi(s)$ from state $s$ as $U^{\pi}(s)$. Then, an _optimal policy_ function $\pi^{\star}$ is one that maximizes the expected utility:

$$\pi^{\star}\left(s\right) = \text{arg max}~U^{\pi}(s)$$

for all $s\in\mathcal{S}$. We can iteratively compute the utility of a policy $\pi$. If the agent makes a single move, the utility will be the reward the agent receives by implementing policy $\pi$:

$$U_{1}^{\pi}(s) = R(s,\pi(s))$$

However, if we let the agent perform two, three, or $k$ possible iterations, we get a _lookahead_ equation which relates the value of 
the utility at iteration $k$ to $k+1$:

$$U_{k+1}^{\pi}(s) = R(s,\pi(s)) + \gamma\sum_{s^{\prime}\in\mathcal{S}}T(s^{\prime} | s, \pi(s))U_{k}^{\pi}(s^{\prime})$$

As $k\rightarrow\infty$ the lookahead utility converges to a stationary value $U^{\pi}(s)$:

````{prf:definition} Value function
:label: defn-policy-evalution

Suppose we have a Markov decision process with the tuple $\left(\mathcal{S}, \mathcal{A}, R_{a}\left(s, s^{\prime}\right), T_{a}\left(s,s^{\prime}\right), \gamma\right)$. Then, the utility of the policy function $\pi$ equals:

```{math}
:label: eqn-converged-policy-eval
U^{\pi}(s) = R(s,\pi(s)) + \gamma\sum_{s^{\prime}\in\mathcal{S}}T(s^{\prime} | s, \pi(s))U^{\pi}(s^{\prime})
```
````

### Value function policies
{prf:ref}`defn-policy-evalution` gives us a method to compute the utility for a particular policy $U^{\pi}(s)$. 
However, we were given the utility and wanted to estimate the policy $\pi(s)$ from that utility. 
Given a utility $U$, we can estimate a policy $\pi(s)$ using the $Q$-function (action-value function):

```{math}
:label: eqn-action-value-function
Q(s,a) = R(s,a) + \gamma\sum_{s^{\prime}\in\mathcal{S}}T(s^{\prime} | s, a)U(s^{\prime})
```

Equation {eq}`eqn-action-value-function` gives a $|\mathcal{S}|\times|\mathcal{A}|$ array, where the utility is given by:

```{math}
:label: eqn-utility-from-Q
U(s) = \max_{a} Q(s,a)
```

and the policy $\pi(s)$ is:

```{math}
:label: eqn-policy-from-Q
\pi(s) = \text{arg}\max_{a}Q(s,a)
```

## Value iteration
In the previous section, we saw how we could develop _a policy_ $\pi(s)$ by looking at the values in the $Q$-array. However, this required the utility vector; thus, we needed to hypothesize a policy that may not be the _optimal policy_. There are two techniques to compute optimal policies, and we'll explore the simpler of the two, namely _value iteration_. 

In _value iteration_, the value function (the vector of utility values) is updated iteratively using the _Bellman update__ procedure:

```{math}
U_{k+1}(s) = \max_{a}\left(R(s,a) + \gamma\sum_{s^{\prime}\in\mathcal{S}}T(s^{\prime} | s, a)U_{k}(s^{\prime})\right)
```

This procedure is guaranteed to converge to the optimal utility vector (value function).  
