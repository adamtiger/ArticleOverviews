# Article Summary

**Title:** LEARNING TO PLAY IN A DAY: FASTER DEEP REINFORCEMENT LEARNING BY OPTIMALITY TIGHTENING <br/>
**Authors:** Frank S. He, Yang Liu, Alexander G. Schwing, Jian Peng <br/>
**Year:** 2016

### Citation:

@article{he2016tightening, <br/>
  author    = {Frank S. He and Yang Liu and Alexander G. Schwing and Jian Peng}, <br/>
  title     = {Learning to Play in a Day: Faster Deep Reinforcement Learning by Optimality Tightening}, <br/>
  journal   = {CoRR}, <br/>
  volume    = {abs/1611.01606}, <br/>
  year      = {2016}, <br/>
  url       = {http://arxiv.org/abs/1611.01606}, <br/>
  archivePrefix = {arXiv}, <br/>
  eprint    = {1611.01606}, <br/>
  timestamp = {Wed, 07 Jun 2017 14:41:31 +0200}, <br/>
  biburl    = {https://dblp.org/rec/bib/journals/corr/HeLSP16}, <br/>
  bibsource = {dblp computer science bibliography, https://dblp.org} <br/>
}

### Abstract:

We propose a novel training algorithm for reinforcement learning which combines
the strength of deep Q-learning with a constrained optimization approach
to tighten optimality and encourage faster reward propagation. Our novel technique
makes deep reinforcement learning more practical by drastically reducing
the training time. We evaluate the performance of our approach on the 49 games
of the challenging Arcade Learning Environment, and report significant improvements
in both training time and accuracy.

## Overview

Here a structured but concise overview on the article is provided.

### Technical background

This article deals with the reduction of the sampling complexity of DQN. 
DQN can require 200 million frames (or steps) to achieve reasonable results on Atari-games. 
he method proposed in the paper is able to decrease this down to 10 million. 
The authors identify that one-step sequences are not enough for efficient bootstrapping because 
it is not able to propagate the rewards fast enough. This is especially true when the reward is sparse (delayed). 
They suggest the following: “Not only do we propagate information from time instances in 
the future to our current state, but also will we pass information from states several steps in the past“. 
Therefore they reformulate the objective of reinforcement learning by introducing an upper and a 
lower bound for Q values then the objective function got two further terms which are active when the constraints 
(upper or bound) are violated (see equation). 

![eq](https://drive.google.com/uc?export=download&id=181nOA6ArhPi2mO4V_mAafnzhxoUrMdg3)

According to the authors this has the following effect on the reward propagation: “We emphasize that the derivatives 
correcting the prediction of Q(s_j; a_j) not only depend on the Q-function from the immediately successive time 
step Q(s_j+1; a) stored in the experience replay memory, but also on more distant time instances if constraints are violated. 
Our proposed formulation and the resulting optimization
technique hence encourage faster reward propagation,…”. 

My view is that the strength is based on that the lower requires future rewards while the upper bound 
requires past rewards (experiences). Therefore a much longer sequence is taken into account during the 
calculation which means more information during training.

### Results, experiments

The test bed was ALE. They compared the original DQN and their algorithm with training on 10 million frames. 
The new algorithm achieves higher results during the 10 M frames long training but surprisingly it can achieve 
better results when compared to the 200 million frames long training of DQN. 
They experimented with some other DQN variants (DQN(\lambda), DQN+return which 
uses the discounted future return as a bound) as well. Still the new algorithm performs better. 
The following image provides a good overall glance:

![comp](https://drive.google.com/uc?export=download&id=1jilVhSD0oDGjJWAdGBMC2piqOUucRTld)
