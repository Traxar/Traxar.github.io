# Kelly criterion generalized

by: Lorenz Auer

## Motivation

Consider the following example: 

## Approach

Let's start by considering a way simpler problem, a single binary bet.

> A **binary bet** has the following defining parameters:
> 
> - **random event** (i.e.: cointoss, diceroll,...)
> - **probability** $p$ (i.e.: $50\%$, ...)
> - **odds** $\Phi$ (i.e.: 2, ...)
> 
> By placing r currency on such a bet. The gambler has to pay r upfront. Then the random event occures. If its outcome matches the desired outcome, which has the given probability of happening. The gambler gets payed out $\Phi\cdot r$. If the outcome is not equal to the desired one. The gambler gets nothing. It should be noted, that there are only 2 possible outcomes either the gambler wins said amount or loses the money.

First of all it should be mentioned that just having a bet with a expected return $\Phi\cdot p\ge1$ is not enough to turn a profit over many rounds. For a demonstation consider the bet with $p=0.5,\Phi=2.25$. Now let's say that the gambler decides to bet $40\%$ of all their belongings each round. Running the numbers one might expect an average return of $+5\%$ each round and hence assume that the gamblers capital will grow in the long run. Here is a simulation of 100 runs each betting 1000 times, each run starts at $1$ currency:

![](C:\Users\Lorenz\AppData\Roaming\marktext\images\2021-07-30-21-56-57-image.png)

This might come as a shocking result since one can see that even though some runs generate a lot of money eventually they all lose roughly $5\%$ per round.

In 1956 J.L. Kelly published a paper regarding this phenomenon, in which he derived the formular nowadays often known as the Kelly Criterion to maximise growth. According to which in this example the gambler is best of betting $10\%$ of all their belongings each round:

![](C:\Users\Lorenz\AppData\Roaming\marktext\images\2021-07-30-22-07-13-image.png)

(Note: Simulation was capped at 10000 to prevent overflow errors)

Logartihmic scale for better visualisation:

![](C:\Users\Lorenz\AppData\Roaming\marktext\images\2021-07-30-22-17-54-image.png)

This is achieved by maximising the geometric mean:

$$
(1-r)^{1-p}(1-r+\Phi\cdot r)^p
$$

with:

$$
r=\frac{\Phi\cdot p-1}{\Phi-1}
$$

Since this will provide the best exponential growth possible.

## General discrete bet

A general discrete bet has the following defining parameters:

- **random event** (i.e.: cointoss, diceroll,...)
  
  the random event has $1\le n\in\N$ different outcomes. (i.e.: 2, 6,...)

- **probabilities** for each possible outcome $p\in \R_{\ge0}^n,\|p\|_1=1$

- **odds** (payout) for each possible outcome $\Phi\in\R_{\ge0}^n$

By placing $r$ currency on such a bet. The gambler has to pay $r$ upfront. Then the random event occures and so the index $0\le i\le n$ is choosen, according to the outcome. The gambler then gets payed out $\Phi_i\times r$.

By $n\to\infty$ we can easily converge to a continous model.

## Software

Download [here](https://traxar.github.io/KellyFinder/download/KellyFinder.zip). (Windows)
