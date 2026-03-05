Map
- regularized more respect to ML
- max the posterior
	- log2 is number of bits of prior
		- is like counting how many bits I need to fit data
	- second term is a penalizer
		- the more complex gets the model
		- the more penalize the objective function

Maximum Likelihood Learning
- joint distribution became marginal products because we assuming independence
- using logarithm to exploit sum instead of product (malconditioned in optimization problem)
- maximum the likelihood in bernoulli example is trivial frequence of head count
- Data driven calculation

Data driven is one of the biggest difference in ML and MAP
- we can't trust ML in low data regime
	- overfitting
	- pure datadriven
- MAP is more helpful because we introduce regularization

MAP
- find parameters s.t maximize posterior and prior
- we use conjugate distributions for the posterior
	- on bernoulli we use beta distribution
	- we cancel out the normalization parameter because is useless on derivative
	- the last part is similiar to ML
		- beta distribution that comes from the prior times the likelihood Bernoulli
		- alpha and beta are hyperparameters
			- alpha number of heads seen at priori
			- beta number of tails seen at priori
		- we injected bias on counts
- we get the full distribution of theta, not the single theta
	- distribution of our parameters
	- not the single parameter
	- so we can make prediction instead of being prisoner of the data

Naive Bayes Classifier
- we are using MAP
	- rewriting posterior as likelihood times prior
	- naive assumption
		- when observing a class ...
	- the marginalazed probability is a matrix of k multinomials
- indicator variable $z_{jk}$ and the other
	- misclassifications gets cancelled out
	- written the likelyhood in terms of parameters