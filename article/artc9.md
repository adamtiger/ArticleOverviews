# Article Summary

**Title:** Reproducibility of Benchmarked Deep Reinforcement Learning Tasks for Continuous Control <br/>
**Authors:** Riashat Islam, Peter Henderson, Maziar Gomrokchi, Doina Precup <br/>
**Year:** 2017

### Citation:

@article{DBLP:journals/corr/abs-1708-04133, <br/>
  author    = {Riashat Islam and <br/>
               Peter Henderson and <br/>
               Maziar Gomrokchi and <br/>
               Doina Precup}, <br/>
  title     = {Reproducibility of Benchmarked Deep Reinforcement Learning Tasks for Continuous Control}, <br/>
  journal   = {CoRR}, <br/>
  volume    = {abs/1708.04133}, <br/>
  year      = {2017}, <br/>
  url       = {http://arxiv.org/abs/1708.04133}, <br/>
  archivePrefix = {arXiv}, <br/>
  eprint    = {1708.04133}, <br/>
  timestamp = {Tue, 17 Oct 2017 12:29:59 +0200}, <br/>
  biburl    = {https://dblp.org/rec/bib/journals/corr/abs-1708-04133}, <br/>
  bibsource = {dblp computer science bibliography, https://dblp.org} 
}

### Abstract:

Policy gradient methods in reinforcement learning have become increasingly prevalent
for state-of-the-art performance in continuous control tasks. Novel methods
typically benchmark against a few key algorithms such as deep deterministic policy
gradients and trust region policy optimization. As such, it is important to
present and use consistent baselines experiments. However, this can be difficult
due to general variance in the algorithms, hyper-parameter tuning, and environment
stochasticity. We investigate and discuss: the significance of hyper-parameters in
policy gradients for continuous control, general variance in the algorithms, and
reproducibility of reported results. We provide guidelines on reporting novel results
as comparisons against baseline methods such that future researchers can make
informed decisions when investigating novel methods.

## Overview

Here a structured but concise overview on the article is provided.

### The motivation

This algorithm deals with the difficulty of comparing deep reinforcement learning algorithms.
They investigates an off-policy policy gradient method (DDPG) and an on-policy PG method (TRPO) on two continuous control problem in MuJoCo: Half-Cheetah and Hopper.
The used metric was the average returns. I think this is the best way to measure the performance of an algorithm.

The goal is to figure out how sensitive is the algorithm for changes in network architecture, batch sizes, hyper parameters and provide a guide to make relevant comparisons.
The article doe not really points out how to compare algorithms but warns to use more attention when reporting results.

### Results, experiments

Effect of policy network architecture:

* For both TRPO and DDPG the preformance can significantly vary according to the architecture.

Effect of batch size:

* For DDPG batch size 32 and 64 causes similar results but 128 causes significant improvements.
* For TRPO the larger batch size also produces better results.

Effect of regularization coefficient (TRPO-specific hyper-parameter):

* It does not cause significant difference in using one particular value of RC over another.

Effect of reward scale (DDPG-specific hyper-parameter):

* This can make DDPG unstable.

Effect of random seeds:

* This has the most dramatic effect!!
* 10 trials with different random seeds but with the same hyper-paramters (which seemedbest).
* They created 2 groups (5-5 random seeds) and they found a significant difference between the two average performance.
* Conclusion: stable results with DDPG on either of the environments cannot be achieved.

Therefore it is important to do the following for better benchmarks:

1. report all possible metrics
2. report all hyper-parameters
3. attempt to use a somewhat optimal set of hyper-parameters
4. average results on a lot of trials.

### Articles referred

This article strongly builds upon the following article: Yan Duan et. al, *Benchmarking deep reinforcement learning for continuous control*, ICML, 2016.
