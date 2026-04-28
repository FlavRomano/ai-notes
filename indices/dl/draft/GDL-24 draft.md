explicit likelihood model
- in bayesian network we have fully visible varaibles, easy to compute the likelihood
	- joint probability
		- maybe big
			- computationally expensive
		- decide proper ordering
	- fully tractable
		- but when inputs are very big e.g image
			- difficult to compute
				- multiplication mess
				- we need to approximate the conditional probability
					- I can use a LSTM
						- we don't compute $P(X_{3} \mid X_{2}, X_{1})$ but $P(X_{3} \mid X_{2}, h_{2})$ 
						- where $h_{2}$ is the second hidden state that contains a compressed view of X_1 and X_2
			- sensible ordering
				- natural ordering 
	- autoregressive model
		- generating p x_1 from a marginal
			- p x_2 from p x_1 ...

decoder only
- invertible transformation
	- generative direction $x=g(z)$
		- decoder of an autoencoder
	- normalizing direction $z = g^{-1}(x)$
- transforming one distribution (data generating distribution) into a gaussian 