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

---

normalizing flows
- gaussian scaling on multiscale nonlinear flow
	- $\theta_{A}$ mean, $\theta_{B}$ sigma

- inverse flow slow == train slow
	- autoregressive flow
- forward flow slow == sampling slow

- limiting the jacobian == limiting the expressivity of the transformation
	- not limiting the jacobian => using the full rank matrix
		- difficult to keep the invertibility
		- but with residual flows (like in ResNet) change all dimensions of z all together
			- residual layer
				- neural layer + residual connection 
				- one for each flow layer
			- still not invertible
				- but if the network is Lipschitz
					- constraint the activation function of the neural network 
					- small changes of $z$ are invertible because of Banach theorem
						- can be reconstructed and inverted
						- theorem tells that we converge to a fixed point
							- the same point $z$ of the forward flow
				- $\theta$ should be constrained enough to cover some holes in the space (small changes)
					- has fixed points (is contractive)
		- training still bad, generation is fine
	- now full rank jacobian
		- not feasible to compute the log likelihood
			- jacobian complicated
		- use a stochastic approximation for the jacobian based on Gaussian
			- stochastic vector multiplicated to the jacobian
			- cheap