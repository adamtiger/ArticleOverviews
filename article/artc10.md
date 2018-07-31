# Article Summary

**Title:** Benchmarking Deep Reinforcement Learning for Continuous Control <br/>
**Authors:** Yan Duan, Xi Chen, Rein Houthooft, John Schulman, Pieter Abbeel <br/>
**Year:** 2016

### Citation:

@article{DBLP:journals/corr/DuanCHSA16, <br/>
  author    = {Yan Duan and <br/>
               Xi Chen and <br/>
               Rein Houthooft and <br/>
               John Schulman and <br/>
               Pieter Abbeel}, <br/>
  title     = {Benchmarking Deep Reinforcement Learning for Continuous Control}, <br/>
  journal   = {CoRR}, <br/>
  volume    = {abs/1604.06778}, <br/>
  year      = {2016}, <br/>
  url       = {http://arxiv.org/abs/1604.06778}, <br/>
  archivePrefix = {arXiv}, <br/>
  eprint    = {1604.06778}, <br/>
  timestamp = {Wed, 07 Jun 2017 14:41:27 +0200}, <br/>
  biburl    = {https://dblp.org/rec/bib/journals/corr/DuanCHSA16}, <br/>
  bibsource = {dblp computer science bibliography, https://dblp.org} <br/>
}

### Abstract:

Recently, researchers have made significant progress combining the advances in deep learning 
for learning feature representations with reinforcement learning. Some notable examples include 
training agents to play Atari games based on raw pixel data and to acquire advanced manipulation 
skills using raw sensory inputs. However, it has been difficult to quantify progress in the domain
of continuous control due to the lack of a commonly adopted benchmark. In this work, we present a 
benchmark suite of continuous control tasks, including classic tasks like cart-pole swing-up, tasks
with very high state and action dimensionality such as 3D humanoid locomotion, tasks with partial
observations, and tasks with hierarchical structure. We report novel findings based on the
systematic evaluation of a range of implemented reinforcement learning algorithms. Both the
benchmark and reference implementations are released at _https://github.com/rllab/rllab_ in order
to facilitate experimental reproducibility and to encourage adoption by other researchers.

## Overview

Here a structured but concise overview on the article is provided.

### Motivation, approach

The article express the significance of the achieved results by combining deep learning methods with RL.
The authors claim the missing standardized and challenging testeds for RL to measure the scientific progress.
A well established, systematic evaluatin and comparison method can help to understand better the current algorithm's strengths and weeknesses.
Therefore they present a benchmark consisting of 31 continuous control tasks which can be devided into four categories:
1. basic tasks: like CartPole problem
2. locomotion tasks: like Half-Cheetah
3. partially observable tasks: three subcategories (limited sensors, noisy observations and delayed actions, system identification)
4. hierarchical tasks: for instance to reuse locomotion skills when exploring the environment.

They mainly use gradient-based policy search methods (REINFORCE, TNPG, RWR, REPS, DDPG, TRPO) and some gradient-free methods (CEM, CMA-ES).
They also provide a reproducible way to choose the hyper-parameters: The criterion for the best hyperparameters is defined as mean(returns) − std(returns).


### Results, experiments

Here are the most important results regarding the algorithms.

REINFORCE: Despite its simplicity, REINFORCE is an
effective algorithm in optimizing deep neural network policies in most basic and locomotion tasks. 
Even for highDOF tasks like Ant, REINFORCE can achieve competitive results.

TNPG and TRPO: Both TNPG and TRPO outperform
other batch algorithms by a large margin on most tasks,
confirming that constraining the change in the policy distribution results in more stable learning.

RWR: They observed empirically that RWR shows fast initial
improvement followed by significant slow-down.

REPS: Especially prone to early convergence to local optima in case of continuous states and actions.

Gradient-free methods: Achieved suprisingly good results.

Partially Observable Tasks: They experimentally verified that recurrent policies can find better solutions than feedforward policies.
