This time we deal with incomplete data
- imputation approach
	- use an average
	- educated guess, biasing the model
		- if is not good, I change and try again
- $c$ is an hidden variable now
- we want to seek a natural grouping
	- no classification
	- distance influence on grouping change guesses

I work with the joint of the visible and the latent variable
- $\theta$ are parameters of different distribution
- I need to marginalize $z$ to get rid of $z$ in the conditional probability in the left
	- I get the expectation

maximize the complete likelihood instead of the incomplete one
- $P(Z\mid X,\theta)$ is the posterior

Expectation maximization
- until the complete likelihood increase
	- I guess and refine value for $Z$
- we get the $Z$ from the expectation summation
	- should be computable
- I use the previous $theta$ to compute the posterior at current iteration
- 2 step iterative algorithm
	1. expectation step
	2. model parameter step
- keep doing it until likelihood changes
	- a theorem ensure improvement and never worsening of the likelihood
		- maximizing a proxy function $Q$ where $Q$ is computed with the $k$ parameters
		- it touches the likelihood function in the same point of $Q$
			- we got a lower bound
			- by maximizing it we can increase indirectly the likelihood $L$
		- we say that ensures monotonic non-decrease
	- we can't compute the $Q$ in close, so we need to estimate that

Gaussian Mixture Models
- marginalizing over all $z$ all possible gaussians
	- I get a final silhouette that is exactly the distribution of $P(X)$
- probability to assign a sample to a class $$P(Z \mid X, \theta)$$ so inference problem, because that's the posterior and we want to calculate that.

To compute GMM likelihood
- once again we use auxiliary indicator variables
	- because in the likelihood formula we would have a log of summation, which is terrible to compute
	- the auxiliary we'll get just the exactly right gaussian for the right sample
		- zero o/w
	- unfortunately they are hyperparameters
- now I can compute the complete log likelihood
	- feasible now, instead of the product summation thing
- but the indicator variables remain unknown
- we can
	- applying expectation of $Z$ wrt the posterior
	- rewriting the complete log likelihood
		- changing the indicator variable
		- with a distribution that tell how likely we generate the j sample with m gaussian
	- we compute the posterior of the model just with its parameters (which are known and observable)