# Article Summary

**Title:** VALUE PREDICTION NETWORK <br/>
**Authors:** J. Oh, S. Singh, H. Lee <br/>
**Year:** 2017

### Citation:

@article{DBLP:journals/corr/OhSL17,
  author    = {Junhyuk Oh and Satinder Singh and Honglak Lee}, <br/>
  title     = {Value Prediction Network}, <br/>
  journal   = {CoRR}, <br/>
  volume    = {abs/1707.03497}, <br/>
  year      = {2017}, <br/>
  url       = {http://arxiv.org/abs/1707.03497}, <br/>
  archivePrefix = {arXiv}, <br/>
  eprint    = {1707.03497}, <br/>
  timestamp = {Sat, 05 Aug 2017 14:56:06 +0200}, <br/>
  biburl    = {http://dblp.org/rec/bib/journals/corr/OhSL17}, <br/>
  bibsource = {dblp computer science bibliography, http://dblp.org} <br/>
}

### Abstract:

This paper proposes a novel deep reinforcement learning (RL) architecture, called
Value Prediction Network (VPN), which integrates model-free and model-based
RL methods into a single neural network. In contrast to typical model-based
RL methods, VPN learns a dynamics model whose abstract states are trained
to make option-conditional predictions of future values (discounted sum of rewards) rather than of future observations. Our experimental results show that
VPN has several advantages over both model-free and model-based baselines in a
stochastic environment where careful planning is required but building an accurate
observation-prediction model is difficult. Furthermore, VPN outperforms Deep
Q-Network (DQN) on several Atari games even with short-lookahead planning,
demonstrating its potential as a new way of learning a good state representation.

## Overview

This article proposes a deep learning version of an integrated architecture.
The integrated architecture integrates learning, planning and prediction. 
The main idea is to use a single network which does the prediction, and the value calculation. 
It is a good idea to use an abstract state representation instead of the original observation 
which has a much bigger dimension and it can happen that not the whole observation space is important for making decisions. 
The encoding into the abstract space is also learned by a neural network. This is the core module. 
If the core module is applied more times a k-step prediction can be gotten. 
The learning architecture takes n-step by following the suggested option of planning in the real environment and 
makes k-step predictions during the trajectory in each step. These predictions are useful to learn the environment 
model (r, γ) and the value prediction faster. At the last step in the trajectory planning happens with *d* planning-depth to 
approximate the target value in the n-step Q-learning (similarity). 
The planning uses roll-outs and restricted branching factor with b most promising options. 
Then the achieved returns are backuped to get the approximation for the state-value. 
The loss function consists of three squared terms: 
1) error in the predicted reward, 
2) error in the predicted value (the target is approximated by planning, like TD-learning) 
3) error in the discounting factor for an option.

Experiments were done on two test beds: 
1) Collecting (the task is to collect goals in a maze like world), 
2) Atari. 

The proposed new architecture outperformed DQN.  

### Articles referred

The following article is referred throughout in this paper: **Oh et. al., VPN, (2017)**. 
