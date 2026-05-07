diffusion models
- variational (elbo involved)
- bidirectional flow
	- a la variational auto encoder (interpretation)
	- forward process, data to noise (gaussian)
		- KL divergence is helpful
		- encoding $x$ to $z$
	- noise to data
		- decoding $z$ to $x$
		- reconstruction
	- latent space $z$ has the same dimension of $x$
		- not very computationally efficient
	- one z for each step of layer of injection
		- $z_{T}$ pure noise

forward diffusion
- fixed model
	- no parameters
	- like in vae but image that the encoder has no parameters
- stochastic process
	- $P(z_{2} \mid z_{1})$
	- ...
	- $P(z_{T} \mid z_{T-1})$
	- we can generalize it to $P(z_{t} \mid z_{t-1})$
		- it's a markov chain
		- $q$ is the transition distribution
			- gaussian with displaced scaled mean and variance
			- the joint distribution factorized to product of smaller distribution
				- due to markov decomposition
	- we start with little noise then hammer a lot of it at the end
		- $\beta$ small at the beginning
		- larger at the ends

diffusion kernel
- shortcut, given $x$ we don't need $z_{t-1}$ to get to $z_{t}$ $$q(z_{t}\mid x)$$
- $\alpha_{t}$ pre-computable schedule
- $z_{t}$ is obtained through $\alpha_{t}$ instead of $\beta$

denoising
- starting from sample from $z_{T}$
	- because we can't look at the whole distribution 
- go to $z_{T-1}$ and so on 
	- reverting time
- use neural network (most of the time a unet or even a transformer) to find something that can approximate $q(z_{t-1}, z_{t})$
	- otherwise is intractable
		- wrt bayes rule we got $q(z_{t-1})$ and $q(z_{t})$
		- which are integrals obtained through marginalization
	- receive in input $z_{t}$ and produce mean and variance (or fixed one if I use $\beta$ like in the slides) of a distribution
	- amortized inference
		- it takes in input also time to know how much of noise is injected at a specific time
			- because the noise change with time
- we use distribution given $z_{t}$ and $x$ to obtain $z_{t-1}$ with mean and variance predicted from the neural network
	- the distribution is almost gaussian thanks to $x$
		- under the assumption of small noise each step
		- otherwise we can't approximate it

training
- maximum likelihood training
	- latent variable model => intractable log likelihood integral 
- use elbo
	- variational distribution $q$
	- $z$'s latent variables
	- first term is reconstruction error
	- second term
		- KL promote the matching of two distribution
		- difference between the gaussian at training time
			- the mean from the neural network should be similiar to the one I know at training time
	- we using the ELBO in an other way
		- $q$ should be the variational distribution but is fixed
			- no parameters
		- we move $P_{\theta}$
			- the predicted one
- practical view
	- knowing the noise and the time $t$ I can reconstruct anything
		- I don't need the mean anymore
	- the neural network can just predict the noise at time t given the estimation of $z_{t}$

trade off
- training is highly parallelizable
- sampling is slower
	- a lot of sequential steps