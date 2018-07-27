# Article Summary

**Title:** INTEGRATED ARCHITECTURES FOR LEARNING, PLANNING, AND REACTING BASED ON APPROXIMATING DYNAMIC PROGRAMMING <br/>
**Authors:** Richard S. Sutton <br/>
**Year:** 1990

### Citation:

@inproceedings{ sutton1990Dyna, <br/>
title={Integrated Architectures for Learning Planning and Reacting
Based on Approximating Dynamic Programming}, <br/>
author={Richard S. Sutton}, <br/>
booktitle={International Conference on Machine Learning}, <br/>
year={1990}, <br/>
}

### Abstract:

This paper extends previous work with Dyna a class of architectures for intelligent systems
based on approximating dynamic programming methods. Dyna architectures integrate
trial-and-error (reinforcement) learning and execution-time planning into a single process
operating alternately on the world and on a learned model of the world. In this paper I
present and show results for two Dyna architectures. The Dyna-PI architecture is based
on dynamic programming's policy iteration method and can be related to existing AI
ideas such as evaluation functions and universal plans (reactive systems). 
Using a navigation task results are shown for a simple
Dyna-PI system that simultaneously learns by trial and error learns a world model and
plans optimal routes using the evolving world model. The Dyna-Q architecture is based
on Watkins's Q-learning a new kind of reinforcement learning. Dyna-Q uses a less 
familiar set of data structures than does Dyna-PI but is arguably simpler to implement and use.
We show that Dyna-Q architectures are easy to adapt for use in changing environments.

## Overview

The article is about two special Dyna architectures: Dyna-PI and Dyna-Q. 
The test bed is a randomly generated maze in a gridworld. 
The environment is deterministic and fully-observable. 
The environment is changing and reward is only received in the goal state. 
The Dyna-PI version is based on a policy iteration. 
It maintains the value function and policy function and the world model as well. 
Dyna-Q maintains only the Q-function. The algorithm switches the real experiences and the simulated experiences. 
After one real experience a lot of modeled one follows. 
Dyna-PI has the problems in changing environment: blocking problem, shortcut problem. 
The reason behind them is the lack of sufficient exploration in the environment. 
Somehow the agent should continually test its environment.
Dyna-Q can address this issues by using the exploration bonus both in the selection rule and in the update rule. 
It is also important that Dyna-Q is based on Q-learning which is an off-policy learning. 
Therefore it is possible to disjoint the exploration and exploitation and that makes easier to maintain the exploration. 
In overall Dyna-Q achieves better results.
