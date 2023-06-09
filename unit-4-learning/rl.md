# Reinforcement Learning

In our discussion of [Markov decision process (MDPs)](../unit-3-planning/mdp.md), we assumed that the transition and reward models were known precisely. However, these models may not be discovered in many actual problems. In these cases, the agent must learn to act through experience, e.g., by observing the outcomes of its actions. Then the agent chooses actions that maximize its long-term accumulation of reward. 

Several challenges must be addressed in cases of uncertain models. First, agents must balance between exploring the world and exploiting knowledge gained through experience. Second, rewards may be received long after decisions have been made. Finally, agents must generalize from limited experience. 

---

 ```{figure} ./figs/Fig-Schematic-RL.pdf
---
height: 260px
name: fig-rl-schematic
---
Schematic of the reinforcement learning (RL) process. An agent takes action $a$ and then observes reward $r$ and changes in the state of the environment ($s\rightarrow{s^{\prime}}$) following the action $a$. 
```

(content:references:basic-concepts-reinforcement-learning)=
## Basic concepts of reinforcement learning
[Reinforcement Learning (RL)](https://en.wikipedia.org/wiki/Reinforcement_learning) agents learn by performing actions in the world and then analyzing the rewards they receive ({numref}`fig-rl-schematic`). Thus, reinforcement learning differs from other machine learning approaches, e.g., [supervised learning](https://en.wikipedia.org/wiki/Supervised_learning) because labeled input/output pairs, e.g., what actions lead to positive rewards are not presented to the agent _a priori_.  Instead, reinforcement learning agents learn what is good or bad by trying different actions. 

Reinforcement learning agents learn optimal choices in different situations by balancing the exploration of their environment, e.g., by taking random actions and watching what happens, with the exploitation of the knowledge they have built up so far, i.e., choosing what the agent thinks is an optimal action based upon previous experience. The balance between exploration and exploitation is one of the critical concepts in reinforcement learning.

(content:references:model-free-reinforcement-learning)=
## Model-free reinforcement learning
Model-free reinforcement learning does not require transition or reward models. Instead, model-free methods, like bandit problems, iteratively construct a policy by interacting with the world. However, unlike bandit problems, model-free reinforcement learning builds the action value function $Q(s, a)$ directly, e.g., by incrementally estimating the action value function $Q(s, a)$ from samples using the [Q-learning approach](https://en.wikipedia.org/wiki/Q-learning). 

### Incremental updates
Model-free methods incrementally estimate the action value function $Q(s, a)$ by sampling the world. To understand the structure of the update procedures, which we'll discuss later, let's take a quick detour and look at how we incrementally estimate the mean of a single variable $X$. Suppose we are interested in computing the mean of $X$ from $m$ samples:

```{math}
:label: eqn-simple-mean
\hat{x}_{m} = \frac{1}{m}\sum_{i=1}^{m}x^{(i)}
```

where $x^{(i)}$ denotes the ith sample. However, model-free RL incrementally updates $Q(s,a)$; thus, we need to develop an incremental estimation calculation. 
Equation {eq}`eqn-simple-mean` can be re-written as:

```{math}
:label: eqn-simple-mean-1
\hat{x}_{m} = \frac{1}{m}\left(x^{(m)}+\sum_{i=1}^{m-1}x^{(i)}\right)
```

but the summation term is mean from $m-1$ samples or:

```{math}
:label: eqn-simple-mean-2
\hat{x}_{m} = \frac{1}{m}\left(x^{(m)}+(m-1)\hat{x}_{m-1}\right)
```

which can be rearranged to give the incremental update expression:

```{math}
:label: eqn-simple-mean-3
\hat{x}_{m} = \hat{x}_{m-1} + \frac{1}{m}\left(x^{(m)}-\hat{x}_{m-1}\right)
```

Equation {eq}`eqn-simple-mean-3` can be generalized to give the incremental update rule ({prf:ref}`defn-incremental-update-rule`):

````{prf:definition} Incremental update rule
:label: defn-incremental-update-rule

Let $\hat{x}_{m-1}$ denote the mean value computed from $m-1$ samples. The value of $\hat{x}_{m}$ given the the next sample $x^{(m)}$ can be written as:

```{math}
:label: eqn-next-sample-mean
\hat{x}_{m} = \hat{x}_{m-1} + \alpha\left(m\right)\left(x^{(m)}-\hat{x}_{m-1}\right)
```

where $\alpha\left(m\right)$ is the learning rate function. The learning rate can be any function of $m$; however, to ensure convergence 
$\alpha\left(m\right)$ must have the properties: the sum of $\alpha\left(m\right)$ as $m\rightarrow\infty$ can be unbounded, but the sum of $\alpha\left(m\right)^{2}$ as $m\rightarrow\infty$ is bounded. 
````

### Q-learning
The Q-learning approach incrementally estimates the action value function $Q(s,a)$ using the action value form of the _Bellman expectation equation_.  From our discussion of [Markov decision process (MDPs)](../unit-3-planning/mdp.md), we know that the action-value function (the $Q$-function) is defined as:

```{math}
Q(s,a) = R(s,a) + \gamma\sum_{s^{\prime}\in\mathcal{S}}T(s^{\prime} | s, a)U(s^{\prime})
```

However, we know that:

```{math}
U(s) = \max_{a} Q(s,a)
```

thus:

```{math}
:label: eqn-bellman-expectation-eqn
Q(s,a) = R(s,a) + \gamma\sum_{s^{\prime}\in\mathcal{S}}T(s^{\prime} | s, a)\left(\max_{a^{\prime}}Q(s^{\prime},a^{\prime})\right)
```

Here's the catch: in a model-free universe, we don't know the rewards or physics of the world, i.e., we don't know the rewards $R(s, a)$ or the probability array $T(s^{\prime} | s, a)$ that appear in Eqn. {eq}`eqn-bellman-expectation-eqn`. Instead of computing the rewards $r$ and transitions from a model, we must estimate them from samples received:

```{math}
Q(s,a) = \mathbb{E}_{r,s^{\prime}}\left[r+\gamma\cdot\max_{a^{\prime}}Q(s^{\prime},a^{\prime})\right]
```
We can use the incremental update rule shown in Eqn. {eq}`eqn-next-sample-mean` to develop an an expression that incrementally updates our estimate of $Q(s,a)$ as more data becomes available: 

```{math}
:label: eqn-Q-learning-update-rule
Q(s,a)\leftarrow{Q(s,a)}+\alpha\left(r+\gamma\max_{a^{\prime}}Q(s^{\prime},a^{\prime}) - Q(s,a)\right)
```

where $\alpha$ denotes a _learning rate hyperparameter_. Putting all these ideas together, gives a Q-learning definition ({prf:ref}`defn-q-learning-defn`):

````{prf:definition} Q-learning 
:label: defn-q-learning-defn

There exists states $s\in\mathcal{S}$ and actions $a\in\mathcal{A}$. The action value function $Q(s,a)$ can be iteratively estimated using the update rule:

```{math}
Q(s,a)\leftarrow{Q(s,a)}+\alpha\left(r+\gamma\max_{a^{\prime}}Q(s^{\prime},a^{\prime}) - Q(s,a)\right)
```

where $\alpha$ denotes the learning rate hyperparameter, and $\gamma$ denotes the discount rate. The policy $\pi(s)$ can be estimated from the action value function:

```{math}
\pi(s) = \text{arg}\max_{a}Q(s,a)
```
````

An algorithm to incrementally update the $Q$-function is given by ({prf:ref}`algo-e-greedy-q-learning`):

```{prf:algorithm} $\epsilon$-greedy Q-learning
:label: algo-e-greedy-q-learning

**Inputs**  the pure exploration parameter $\epsilon$, the number of time periods in the horizon $T$, the state space $\mathcal{S}$, the action space $\mathcal{A}$ and the initial state $s$.

**Outputs** the $Q(s,a)$ array

**Initialize**
1. set $Q(s,a)\leftarrow\text{zeros}(|\mathcal{S}|,|\mathcal{A}|)$

**Main**
1. for t $\in$ 1 to T
    1. if rand() $<\epsilon$
        1. Select random action: $a_{t}\sim\text{Uniform}(\mathcal{A})$
    1. else
        1. Select action: $a_{t}\leftarrow\text{arg}\max_{a}Q(s,a)$
    
    1. Apply $a_{t}$: observe the reward $r_{t}$ and the state $s^{\prime}$
    1. Update $Q(s,a)$:
        1. $Q(s,a)\leftarrow{Q(s,a)}+\alpha\left(r+\gamma\max_{a^{\prime}}Q(s^{\prime},a^{\prime}) - Q(s,a)\right)$
    1. Update state:
        1. set $s\leftarrow{s}^{\prime}$

**Return**
$Q(s,a)$
```
