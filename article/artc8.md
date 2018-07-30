# Article Summary

**Title:** How Many Random Seeds? Statistical Power Analysis in Deep Reinforcement Learning Experiments <br/>
**Authors:** Cédric Colas, Olivier Sigaud and Pierre-Yves Oudeyer <br/>
**Year:** 2018

### Citation:

@ARTICLE{
2018arXiv180608295C, </br>
author = {{Colas}, C. and {Sigaud}, O. and {Oudeyer}, P.-Y.}, </br>
title = "{How Many Random Seeds? Statistical Power Analysis in Deep Reinforcement Learning Experiments}", </br>
journal = {ArXiv e-prints}, </br>
archivePrefix = "arXiv", </br>
eprint = {1806.08295}, </br>
keywords = {Computer Science - Machine Learning, Statistics - Machine Learning}, </br>
year = 2018, </br>
month = jun, </br>
adsurl = {http://adsabs.harvard.edu/abs/2018arXiv180608295C}, </br>
adsnote = {Provided by the SAO/NASA Astrophysics Data System} </br>
}

### Abstract:

Consistently checking the statistical significance of experimental results
is one of the mandatory methodological steps to address the so-called 
"reproducibility crisis" in deep reinforcement learning. In this tutorial paper,
we explain how the number of random seeds relates to the probabilities of
statistical errors. For both the t-test and the bootstrap confidence interval
test, we recall theoretical guidelines to determine the number of random
seeds one should use to provide a statistically significant comparison of
the performance of two algorithms. Finally, we discuss the influence of
deviations from the assumptions usually made by statistical tests. We
show that they can lead to inaccurate evaluations of statistical errors and
provide guidelines to counter these negative effects. We make our code
available to perform the tests.

## Overview

Here a structured but concise overview on the article is provided.

### Technical background

The paper deals with finding a method to consistently compare deep reinforcement learning algorithms. 
This is a difficult task due to the high variance in the performance accross different evaluations. 
Most of the deep reinforcement learning algorithms are sensitive to even the random seeds.
Random generators are used for initializing the networks, to drive the stochasticity of the environment end others.
The main focus is on how to choose the number of seeds for evaluation.
Each seed is used for an evaluation then the final result is derived from averaging the unique performances.
The authors uses two techniques to address this problem. 
They investigates the Welch's t-test and the boostrap method to determine confidence intervalls and statistical power.
Otherwise the article starts with a good tutorial about difference testing.

### Results, experiments

The most interesting findings:

* The boostrap test is sensitive to small sample sizes.
* The t-test might slightly under-evaluate the type-I error for non-normal data.
* Inaccuracies in the estimation of the empirical standard deviations s1 and s2 due to low sample size might lead to large errors in the computation of beta.

### Articles referred

The article refers a lot of times to the following two articles: Islam et. al., *Reproducibility of Benchmarked Deep Reinforcement Learning Tasks for Continuous Control*, (2017) and Henderson et. al., *Deep Reinforcement Learning that Matters*, (2017). 
