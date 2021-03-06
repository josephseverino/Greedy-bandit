
# Inroduction: Multi-Armed Bandit Problem

<span style="font-family:Papyrus"> The multi-armed bandit problem is a fundamental problem in reinforcement learning. The basic problem involves three (this could be generalized to N arms) different distributions (bandits) with static means and variances. The goal to this problem is finding an agent (algorythm) that can estimate the means and variances of the bandits with some degree of certainty in the most most optimal amount of time for any given bandits (distributions).
</span>

#### *Why "Bandits"?*

<span style="font-family:Papyrus"> Back in the good ole days of gambling, people would flock to the casinos to get a chance to wage their hard earned money on the deceptive slot machines by pulling a long arm. Now we use more high-tech touch screens to mimic these simulations of gambling. Of course, no casino would be profitable if there underlying distributions to each machine wasn't atleast slightly in the faover of the casino's. Thus, the name multi-armed "bandit".
</span>

## The Problem

<span style="font-family:Papyrus"> The problem I am exploring is with three different bandits initialized with normal distributions. Later I will explore a more complicated version of the problem which uses other distributions (e.g. Exponential, Poisson etc.). Below is the order in which I will Explore this problem.
</span>

- [x] Introduction
- [ ] Explore large and small values of Epsilon
- [ ] Explore normal distributions with closer means
- [ ] Conclusion of my findings


### Explore Epsilon Values
- [x] Explore large and small values of Epsilon

```python
c_25 = run_experiment(1.0,2.0,3.0, 0.5, 100000)
c_25 = run_experiment(1.0,2.0,3.0, 0.25, 100000)
c_1 = run_experiment(1.0,2.0,3.0, 0.1, 100000)
c_05 = run_experiment(1.0,2.0,3.0, 0.05, 100000)
c_01 = run_experiment(1.0,2.0,3.0, 0.01, 100000)
c_001 = run_experiment(1.0,2.0,3.0, 0.001, 100000)

```
<p align="center">
  <h3>Compare Epsilon and Convergance </>
  <img src="graphs_bandit_1.png" )
</p>

<div>
  
| Epsilon       | Long Term Payout   | Start of Convergance |
| ------------- |:------------------:| --------------------:|
| 0.001         |   2.98424162       |    ≈ 2000            |
| 0.01          |   2.98545949       |    ≈ 200             |
| 0.05          |   2.94623982       |    ≈ 30              |
| 0.1           |   2.89199996       |    ≈ 40              |
| 0.25          |   2.74934096       |    NA                |
| 0.50          |   2.49796348       |    NA                |

</div>


### Small vs. Big Epsilon
<span style="font-family:Papyrus"> We can see from the graphs above that as you decrease epsilon you increase your long term payout except once you get to eps = .001. Here, the payout decreases slightly. This could be due  to the psuedo-random generation of values. Either way, we can see it won't benifit that much. Additionally, we don't want to be overconfident in the case we have really close means or weird distributions with high variance, which ultumitely means closer means. Another thing to note here is that higher values of epsilon (i.e.eps = .25 and greater) don't actually converge on the correct bandit. This is due to over-exploration. When an agent indefinteley chooses the other two bandit 25 percent of the time or greater than your long term payout be attracted to a lower payout since it isn't always picking the higher mean payout.
</span>

#### Closer Means 
- [x] Explore normal distributions with closer means

<span style="font-family:Papyrus"> As we decreased the differences between the means notice that we still are able to converge on the highest bandit. This seems to be due to the fact that we are iterating 100,000 times to collect enough of a sample size for each of our epsilon values. Let's explore this further with a few calculations and estimates. See table below.
</span>

| Epsilon | Prob 100000 | Est of 1.05 |Prob 10000| Est of 1.05 |
| ------- |:-----------:| -----------:|:--------:|:-----------:|
| 0.001   |      33.33  |     .88     |   3.33   |    .27      |
| 0.005   |      166.67 |    1.21     |  16.6    |   1.13      |
| 0.01    |     333.33  |    1.07     |  33.3    |   .96       |
| 0.05    |    1666.67  |    1.06     |  166.6   |   1.16      |
| 0.1     |    3333.33  |    1.06     |  333.3   |   1.08      |
| 0.15    |      5000   |    1.04     |  500     |   1.01      |
#### Variance
<span style="font-family:Papyrus"> From the above chart we can see larger sample sizes such as 100,000 explore more of the other bandits even with low epsilon values. Although, the optimal epsilon seemed to be around .01 to .1. These looked to be the best estimates of the normal distribution with mean 1.05. Thus, these look to have lowest variance with there estimates. Probability given N (100,000 and 10,000) iterations were calculated by taking epsilon times N divided by three, which is the probability of exploring one of other bandits given its respective epsilon. In thoery the larger the sample size the better approximation to the mean we get. However, the cost to sample larger numbers could be costly, so we must minimize that as much as possible.
</span>


## Conclusion
- [x] Conclusion: What I learned.

<span style="font-family:Papyrus"> After doing many experiments I was able to learn a few things about this problem. First, epsilon in this case is the probability that were explore the bandits that look to have a smaller sample mean. Thus, we call this the epsilon-greedy problem. Alternativly, one minus epsilon equals the probability that the agent will eploit the perceived largest sample mean. Next, I noticed higher eploration of all the bandits produces lower variance of mean estimates. Consequently, there are two ways to collect larger samples of all the bandits. One is by increasing your epsilon values and two is by increasing the number of iterations you play with the bandits. The downside to increasing epsilon too much was it would never converge on the highest bandit. The downside to larger iterations of play is it may be costly in real-life practice. Thus, the optimal range for epsilon was from .01 to .1. Although, it seemed reasonable to use a psuedo-decay epsilon to maximize effectiveness of minimizing variance of sample means and maximizing the highest returns. I am still working on the last problem, but see code for more info related to this problem.  
</span>

