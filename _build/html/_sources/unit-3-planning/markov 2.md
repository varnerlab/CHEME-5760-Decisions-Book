# Markov Chains
Markov chains take their name from the Russian mathematician [Andrey Markov](https://en.wikipedia.org/wiki/Andrey_Markov). Markov chains are a stochastic model which describes a sequence of possible events in which the probability of each event depends only on the system state in the previous event.

In this lecture:

* We will discuss {ref}`content:references:markov-chains` and discrete time {ref}`content:references:structure-of-an-hmm`, which are approaches for modeling the evolution of a stochastic system as a series of possible events.

---

(content:references:markov-chains)=
## Discrete-time Markov chains
A Markov chain is a stochastic model describing a sequence of possible events where the probability of each of these events depends only on the system’s current state and not on past system states. A system's state space and time (much like a probability) can be either discrete or continuous; for most of the applications we'll be interested in, we'll focus on discrete time and discrete finite state spaces.

A discrete-time Markov chain is a sequence of random variables $X_{1}$, $X_{2}$, $X_{3}$, ..., $X_{n}$ that have the [Markov property](https://en.wikipedia.org/wiki/Markov_property), i.e., the probability of moving to the _next state_ depends only on the _present state_ and not on the _previous states_:

```{math}
:label: eqn-markov-property
P(X_{n+1} = x | X_{1}=x_{1}, \dots, X_{n}=x_{n}) = P(X_{n+1} = x | X_{n}=y)
```

where _states_ refer to a finite set of discrete values in which the system can exist.  If the state space is finite, the transition probability distribution, i.e., the probability of moving from the state(s) $i\rightarrow{j}$, can be encoded in the transition matrix $\mathbf{P}$. Elements of $\mathbf{P}$, denoted as $p_{ij}$, encode the probability of moving from state $i\rightarrow{j}$ during the next time step:

```{math}
:label: eqn-transition-prob-matrix
p_{ij} = P(X_{n+1}~=~j~|~X_{n}~=~i)
```

The transition matrix $\mathbf{P}$ has interesting properties. First, the rows of transition matrix $\mathbf{P}$ must sum to unity, i.e., each row encodes the probability of all possible outcomes. Thus, it must sum to one. Second, if the transition matrix  $\mathbf{P}$ is time-invariant, then $\mathbf{P}$ is the same at each step. 

(content:references:structure-of-an-hmm)=
## Hidden Markov Models (HMMs)
Hidden Markov models (HMMs) are statistical models in which the system being modeled is assumed to be a Markov process with unobservable states but observable outcomes. HMMs have the same structural components as a standard Markov chain model, but each hidden state can be thought of as sending an observable single. HMMs are widely used in many disciplines to model uncertain systems and situations.