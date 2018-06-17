# Multi-Armed Bandit Problem

##### The multi-armed bandit problem is a fundamental problem in reinforcement learning. The basic problem involves three (this could be generalized to N arms) different distributions (bandits) with static means and variances. The goal to this problem is finding an agent (algorythm) that can estimate the means and variances of the bandits with some degree of certainty in the most most optimal amount of time for any given bandits (distributions).

### Why "Bandits"?

##### Back in the good ole days of gambling, people would flock to the casinos to get a chance to wage their hard earned money on the deceptive slot machines by pulling a long arm. Now we use more high-tech touch screens to mimic these simulations of gambling. Of course, no casino would be profitable if there underlying distributions to each machine wasn't atleast slightly in the faover of the casino's. Thus, the name multi-armed "bandit".

## The Problem

##### The problem I am exploring is with three different bandits initialized with normal distributions. Later I will explore a more complicated version of the problem which uses other distributions (e.g. Exponential, Poisson etc.). Below is the order in which I will Explore this problem.

1. Explore large and small values of Epsilon
2. Explore normal distributions with closer means
3. Explore variance
4. Generalize agent based on exploration
5. Use non-parametized tests to estimated means of bandits
6. Conclusion of my findings
