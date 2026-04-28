manifold learning setting
- vector of the manifold are gradient of the log likelihood
	- aka score

latent aspects of a digit
- size, style...
- I can capture them with a vector of latent variables $z$
	- continuous one
		- intractable on P thehta of x given z
		- we need an approximation (variational elarning)
- probabilistic mapping == conditional probability

variational approximation
- Q and P needs to be Gaussians for KL
- noisy gradient => intractable
- variational function
	- is the encoder
	- with phi as parameters
- reconstruction term
	- push the mean and sigma inside the Gaussian
- regularization term
	- the first gaussian should be near as possible to the Normal distribution
		- the Normal distribution is not informed by input
		- we train z to be consisted to a Normal $\mathcal{N}(0,1)$
	- so penalizes the log likelihood by losing information on inputs in the encoder distribution

we can't use variational autoencoder to compute the likelihood of input, still intractable => it's just an easy way to sample data (not very high quality one, we have GAN for that) => good model for representational learning

smooth mapping of $z$ =>we learn an approximation of the data manifold (at least of the factor of variation of data $z$ considered) => organized latent space for representation learning (two points are closer in latent space so they have closer meaning).