# Article Summary

**Title:** UNIVERSAL AGENT FOR DISENTANGLING ENVIRONMENTS AND TASKS <br/>
**Authors:** Jiayuan Mao, Honghua Dong, Joseph J. Lim <br/>
**Year:** 2018

### Citation:

@inproceedings{
mao2018universal,<br/>
title={Universal Agent for Disentangling Environments and Tasks},<br/>
author={Jiayuan Mao and Honghua Dong and Joseph J. Lim},<br/>
booktitle={International Conference on Learning Representations},<br/>
year={2018},<br/>
url={https://openreview.net/forum?id=B1mvVm-C-},<br/>
}

### Abstract:

Recent state-of-the-art reinforcement learning algorithms are trained under the
goal of excelling in one specific task. Hence, both environment and task specific
knowledge are entangled into one framework. However, there are often scenarios
where the environment (e.g. the physical world) is fixed while only the target task
changes. Hence, borrowing the idea from hierarchical reinforcement learning, we
propose a framework that disentangles task and environment specific knowledge
by separating them into two units. The environment-specific unit handles how to
move from one state to the target state; and the task-specific unit plans for the next
target state given a specific task. The extensive results in simulators indicate that
our method can efficiently separate and learn two independent units, and also adapt
to a new task more efficiently than the state-of-the-art methods.

## Overview

Here a structured but concise overview on the article is provided.

### Technical background

This paper deals with an approach to disentangle the learning process into two units. The first one learns environment specific knowledge while the second unit helps to learn a specific task. At the technical level they define a **path function** and a **goal function**, respectively. The path function takes a current state (s) and a goal state (s’) as arguments then gives the required first action to take in order to get to s’.  So the path function does not give a sequence of actions at once but only an action. Then s will change and the path function will give a new action. In order to train the path function, a pseudo environment is defined with a reward function specified for s’. So the reward is +1 when the goal state is achieved and -1 when not. The last one encourages to finding the shortest path. Then training the path function has high freedom regarding the chosen RL algorithm. The article does not emphasize the chosen algorithm to train the path function but in my opinion it happened as part of an A3C. 

The goal function takes the current state (s) and outputs the corresponding goal state in the feature space. Two main methods are introduced to train the goal function: training with back-propagation and reducing it to a control problem. The first one uses the policy gradient with a slight modification. (The gradient corresponds only to the path function which incorporates the goal function in this case.) The second one puts the goal function into the RL framework with continuous action space. Here the mapping from the state space (which describes the environment) into a latent state space can be chosen in the different ways. The paper investigates 5 different methods. There are some further details like curriculum learning.

### Results, experiments

This paper made a lot of comparison with a base-line A3C implementation. 

*Lava world:* they analyzed the path function how easily it is able to generalize over the distance between the start and goal state. They also investigated the effect of the mapping function for the quality of the path function.

*Reachibility task:* Faster learning was experienced for the universal agent. 

*Knowledge transfer:* Two types of knowledge transfer were examined. Transfer from exploration, where only the sate, action and next state was used but the reward was given by the reward function defined in section 2.1. This was tried in Reachibility. The second type was transfer across multiple tasks. This was tried on Taxi.

*Atari 2600 games:* They investigated the knowledge transfer from other tasks which means new tasks were defined from the original Atari envrionments (JourneyEscape, Riverraid, UpNDown, Alien) and each was solved by using the same path function.

### Articles referred

The following article is referred throughout in this paper: **Pathak et. al.(2017)**. This was mentioned in connection with curiosity-driven RL.

