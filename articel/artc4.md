# Article Summary

**Title:** POLICY DISTRIBUTION <br/>
**Authors:** Rusu et. al. <br/>
**Year:** 2015

### Citation:

@article{DBLP:journals/corr/RusuCGDKPMKH15, <br/>
  author    = {Andrei A. Rusu and
               Sergio Gomez Colmenarejo and
               {\c{C}}aglar G{\"{u}}l{\c{c}}ehre and
               Guillaume Desjardins and
               James Kirkpatrick and
               Razvan Pascanu and
               Volodymyr Mnih and
               Koray Kavukcuoglu and
               Raia Hadsell}, <br/>
  title     = {Policy Distillation}, <br/>
  journal   = {CoRR}, <br/>
  volume    = {abs/1511.06295}, <br/>
  year      = {2015}, <br/>
  url       = {http://arxiv.org/abs/1511.06295}, <br/>
  archivePrefix = {arXiv}, <br/>
  eprint    = {1511.06295}, <br/>
  timestamp = {Wed, 07 Jun 2017 14:40:50 +0200}, <br/>
  biburl    = {http://dblp.org/rec/bib/journals/corr/RusuCGDKPMKH15}, <br/>
  bibsource = {dblp computer science bibliography, http://dblp.org} <br/>
}



### Abstract:

Policies for complex visual tasks have been successfully learned with deep reinforcement learning, 
using an approach called deep Q-networks (DQN), but relatively large (task-specific) networks and 
extensive training are needed to achieve
good performance. In this work, we present a novel method called policy distillation that can be used to extract 
the policy of a reinforcement learning agent
and train a new network that performs at the expert level while being dramatically smaller and more efficient. 
Furthermore, the same method can be used to
consolidate multiple task-specific policies into a single policy. We demonstrate
these claims using the Atari domain and show that the multi-task distilled agent
outperforms the single-task teachers as well as a jointly-trained DQN agent.

## Overview

The goal of this article is to show a methodology for transfer the knowledge into a smaller network but with remaining performance. 
The main idea is to use a teacher and a student network. It was shown that the loss function is important to choose in the right way. 
A KL-divergence based loss function was chosen with softmax. 
The distillation works in a way that the teacher network generates observation and action-value sample pairs which feed into the neural network. 
In case of a multi-task setting, different agents are applied to learn the policy for different environments and after that each agent generates samples into memory buffers. 
The single student network then trained by using these memory buffers sequentially. 
The article investigates a single-game policy distillation, model compression, multi-game policy distillation and online policy distillation. 
The base-line is the DQN: it is the way to train the agent in the environment and the base for comparison as well. 
The results are convincing.
