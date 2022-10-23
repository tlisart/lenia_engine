# Lenia Engine (LE)

There are multiple instances and approaches to computational life sciences and most of the time those are given as exercices to many students of computer science. This project is a side project to not lose some of my programming reflexes and at the same time dabble a bit with the '''Ŕust''' programming language. 

Being the first Rust project I am starting, bugs and failure to comply with some good practices are ineviable, but let's see what we can learn and if we can discover something interesting in the real of logic creatures! 


## What are lenias anyways and what are day, are they out to get you ? 

Lenia is a generalization of no-player games such as Conway's Game Of Life that a lot of people are aware of. Lenia offers a lot of different, suprising and complex emergent patterns in comparison to other game of lifes, it has some interesting properties that one can read on the [open science](https://chakazul.github.io/lenia.html) page. The gliders and other structures have been referenced and is still an active field of research. 

Without further addue, let's get intro the mathematics and principles of Lenia and how we can do some basic research on it to discover some numerical organisms ! 

## All the theory at once 

Being a cellular automata, Lenia updates it's state to discover the next state. In this particular case, the world is not divided into binary grids (cells being alive or dead) each iteration is an output of the previous one through some function. 


Let $\mathcal{L}$ be a discrete lattice with $S^\mathcal{L}$ states. Let also $\psi$ be a _global_ rule, i.e. the rule representing the application of all local rules over the lattice (over every _site_ of the lattice). The particularity with Lenia is that it generalizes Conway's Game of Life, i.e. time **and** space are both discretized up to a certain resolution but considered continuous to the stable limit. If $A^0$ is the initial state of the lattice, the time step is written $\Delta t$ where then the time *resolution* is given by $T = \frac{1}{\Delta t}$

$$
\psi(A^0) = A^{\Delta t}..., \psi(A^t) = A^{t + N\Delta t}
$$

$N$ being the amount of time steps taken. In the case of Lenia, the ensemble of possible states per site is not limited to $\{0, 1\}$ but written in all generality as $\{0, 1, ... P - 1, P\}$ where $P\in \mathbb{Z}$. For symplicity and handling of numbers we chose to represent those states as $\Delta p = \frac{1}{P}$. A state can thus for example be represented as (for example $P = 5$, $A^t(x) = [0.04, 0.6, 1, 0.6]$). 

**It is a cellular automata, how do we deal with neiborhoods then ?**

In the classic Conway's game of life, one uses the 9 cells around the cell being tested to evaluate whether or not the tried cell has to be added or removed. In the context of Lenia those particularities are being generalized introducing discontinious and continuous aspects. In the case of Lenia we are dealing with distance circle or a ball of radius $R$ centered on a site $x$. We define thus the ball: 

$$
\mathcal{N} = \{x \in \mathcal{L} : ||x||_2 \leq R\}
$$

Two things to note then: first the site itself can be included in the ball vector, second the value is not an absolute position but a relative position depending on any given site.

At this point it is important to realize there is a discrete and continuous version of Lenia. Here we'll start by the discrete version then generalize it to continuous. in both cases however we are applying the same transform: 

1. Defining a convolution kernel $K$, such as $K : \mathcal{N} \xrightarrow[]{} S$, this step computes the **potential distribution** of the lenia, computed with the convolution operation:

$$
U^t(x) = K \ast A^t(x)
$$
2. 




