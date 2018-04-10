# Article Summary

**Title:** TREEQN AND ATREEC: DIFFERENTIABLE TREE PLANNING FOR DEEP REINFORCEMENT LEARNING <br/>
**Authors:** G. Farquhar, M. Igl, T. Rocktachel, S. Whiteson <br/>
**Year:** 2017

### Citation:

@article{DBLP:journals/corr/abs-1710-11417,
  author    = {Gregory Farquhar and
               Tim Rockt{\"{a}}schel and
               Maximilian Igl and
               Shimon Whiteson}, <br/>
  title     = {TreeQN and ATreeC: Differentiable Tree Planning for Deep Reinforcement Learning}, <br/>
  journal   = {CoRR}, <br/>
  volume    = {abs/1710.11417}, <br/>
  year      = {2017}, <br/>
  url       = {http://arxiv.org/abs/1710.11417}, <br/>
  archivePrefix = {arXiv}, <br/>
  eprint    = {1710.11417}, <br/>
  timestamp = {Thu, 02 Nov 2017 14:25:36 +0100}, <br/>
  biburl    = {http://dblp.org/rec/bib/journals/corr/abs-1710-11417}, <br/>
  bibsource = {dblp computer science bibliography, http://dblp.org} <br/>
}


### Abstract:

Combining deep model-free reinforcement learning with on-line planning is a
promising approach to building on the successes of deep RL. On-line planning with
look-ahead trees has proven successful in environments where transition models are
known a priori. However, in complex environments where transition models need
to be learned from data, the deficiencies of learned models have limited their utility
for planning. To address these challenges, we propose TreeQN, a differentiable,
recursive, tree-structured model that serves as a drop-in replacement for any value
function network in deep RL with discrete actions. TreeQN dynamically constructs
a tree by recursively applying a transition model in a learned abstract state space
and then aggregating predicted rewards and state-values using a tree backup to
estimate Q-values. We also propose ATreeC, an actor-critic variant that augments
TreeQN with a softmax layer to form a stochastic policy network. Both approaches
are trained end-to-end, such that the learned model is optimised for its actual use
in the planner. We show that TreeQN and ATreeC outperform n-step DQN and
A2C on a box-pushing task, as well as n-step DQN and value prediction networks
(Oh et al., 2017) on multiple Atari games, with deeper trees often outperforming
shallower ones. We also present a qualitative analysis that sheds light on the trees
learned by TreeQN.

## Overview

The article addresses the claim that combining model-free learning with on-line planning would result in better performance. 
The problem is that learning accurate model in a high dimensional space is very difficult which cause huge inaccuracies in the long run. 
They assume that extra computation regarding inferencing the Q-value is better than sampling more. 
Two architectures are introduced with minor differences: TreeQN and ATreeC. 
The main idea is to use two consecutive modules: 
1) do some look ahead based on the possible actions and create a tree with the learnt model, 
2) for the given end points of the tree calculate the corresponding values then propagate back these values with discounted rewards to get the Q-value. 

ATreeC extends this by applying a softmax for the Q in order to get a stochastic policy and a simple fully-connected layer to get the critic (single scalar value for describing how good is the policy).
Each element of the model is differentiable therefore the training is end-to-end. The authors performed nice experiments on Box pushing and Atari.



### Articles referred

The following article is referred throughout in this paper: **Oh et. al., VPN, (2017)**. 
