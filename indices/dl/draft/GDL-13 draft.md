approximating expectations
- assess $f$ over a distribution using the expectation
- when close form is impossible (like posterior in LDA)
	- we don't look at $p$ but at the $L$ samples $X$
	- approximation through empirical mean, average of the function
- we approach the actual expectation with $L \to \infty$ , so with enough samples we are good to go
	- reasonable good approximation

Is it possible to replace learning with just sampling?
- we can generating parameters for a distribution with sampling
- instead of finding parameters by EM or other form of maximization
	- I can generate them by sampling them from a distribution
- in LDA we can learn the model parameters by sampling
	- not really from the real distribution
		- because it's very complicated and unfeasible
	- but still good and computational feasible

the sampler will not be operating on the true probability distribution
- the sampler use a sampling distribution $\tilde{p}$
	- that are not equals to the true distribution $p\neq \tilde{p}$
- we want low variance (desirable)
	- good estimation on average with few example
		- we pick always from a neighborhood
	- given the variance of the estimator, if is low $\hat{f}(X)$ is always close to its expected value
	- we need ==samples independence== to guarantee low variance
		- the sampler needs to produce samples that are independent from each other
- we want unbiased (desirable)
	- so the samples are correct
	- the sampling distribution holds $$\mathbb{E}_{\tilde{p}(X)}[\hat{f}_{X}] = \mathbb{E}_{p(x)}[f(x)]$$
		- same marginals

ancestor sampling
- sample ancestor first
	- we impose a sampling ordering on the naive multivariate sampling
	- we can sample parentless random variables in parallel
- we have problem on colliders
	- if we observed the one at the center (the evidence)
	- then we got the parents dependant
		- so we don't have partial ordering anymore
		- we need to sample both of them 
		- yet another exponential problem

approximate samplers
- we need them because ancestor sampling fails with evidence

Gibbs Sampling
- approximate sampler
- works perfect with evidence
- because all evidence became fixed columns
	- they never change
	- we do less computation
- but the samples here are not independent
	- the current sample has just one variable different than the previous sample
	- a la' Markov Chain
		- we introduce dependency, is it cool?
			- not really
			- we get high variance (not cool)
		- with update delay and editing operation (burning period) we can in some way lower the variance, but it's just too simple to be useful
			- never take two consecutive samples
- Gibbs sampling works thanks to Bayesian Network
	- if we sample $A$ and keep fix the blanket of $A$
		- we can parallelize the other sampling out the markov blanket of $A$ other random variables
		- samples become less correlated
		- structured Gibbs sampling
	- so can be a valid sampling procedure but only with infinite samples
	- trade off between quality of the sample and how many we can sample very quickly (to counteract the variance)
		- no free lunch theorem

MCMC sampling framework
- general framework in which Gibbs sampling is a specialization
- the implementations differs on the choice of $q$ state transition

LDA Gibbs Sampling
- LDA is made of random variables
	- we can sample random variables
		- in a cascade way from beta to theta
		- repreat until convergence
		- the ordering of sample is not random
			- first $z$ ...
- in principle we can learn by sampling
- 