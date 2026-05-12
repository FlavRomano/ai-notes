diffusion models are score matchers
- predicting the score
	- moving in the opposite direction of the scaled injected noise

score
- get rid of partition function $Z_{\theta}$ in exponential family probability distribution
	- good
- in general is the derivative of $f_{\theta}(z)$ given a exponential distribution
- we can learn the score
	- without an extra noise term we don't promote diversity
	- different noises sample can lead to the sample original image
		- model collapsing
		- learn the direction to follow to get the output image
			- the vector that points to the $z_{t-1}$
	- we don't have the data generating distribution 
		- we can't compute the score
		- approximation through Denoising Score Matching
			- use a different score $\tilde{z}$ noisy and $z$ $$p(\tilde{z} \mid z) = \mathcal{N}(z, \sigma^2)$$
			- we created a treatable constructed distribution
	- the neural network learns to output the $L_{DSM}$
		- learn a bypass score
		- how much to push $\tilde{x}$ out the manifold from original sample $x$ is given from $\sigma$ which scales the noise $\epsilon$
			- tricky part
	- the training can be parallelize
		- not so much different from diffusion models 

how to get the scale for score
- we don't have discrete noise steps anymore
	- continuous steps 
	- small infinitesimal steps towards infinity
		- infinitesimal variation that we can use to train the model in the forward part
		- then use the predicted score to go from noise to original distribution
	- the difficult part is the Brownian noise
		- we can get rid of it
		- we get different trajectories but we obtain to the same distribution backward anyways
			- because we only care to get to the data generating distribution as close as possible starting from the noise
		- analogy to normalizing flows

we still don't know the score because of $p_{t}(z)$, do we need it anyway?
- no, we can train an nn to predict velocity directly instead
	- **easier** continuous normalizing flows
		- is a velocity model
		- morph one distr. to multimodal distribution
		- predicting instantanuous velocity
		- easier because the nn layers doesn't require invertibility
	- flow matching (aka matching velocity)
	- more general than diffusion models
		- we have less constraints
- every point of transformation is just the velocity field $v_{\theta}$ predicted by the neural network
- rectified flows 
	- we use conditional velocity to approximate ground truth velocity
		- with just sample from the noise distribution and a point of data generative distribution
- generalizing rectified flows
	- we use gaussian interpolations between the two just choosing alpha and sigma with a schedule
		- $\alpha$ how much content i'm preserving at time $\tau$
		- $\sigma$ how much noise i'm injecting
	- highly parallel
		- easy training
- sampling is sequencial
	- solve cauchy problem
	- but easy anyway
		- easier than diffusion models

