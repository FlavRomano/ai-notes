factors of variations
- e.g in image to keep the visual content meaningful I can't random change pixel in the image
	- but maybe I can change portion of image and still keeps some semantic content

from a neural network prospective
- train a nn that can generate new samples
	- unknown underline groundtruth data generated distribution

autoencoder
- z (good embedding) is less expressive then x (information bottleneck)
	- get rid of the noise 
	- less sparsity
	- dimensionality reduction effect
- decoder can reconstruct x from z thanks to the de-noising contribution of the encoder

sparse autoencoder
- penalize too many active neuron on z
- prior added to likelihood has an regularization effection on ML

denoising autoencoder
- we add noise to x
	- apply gaussian noise (small variance!!)
	- the x hat
- train the nn to reconstruct $x$ starting from $\hat{x}$

nn works and dl works
- because we take manifold hypothesis on our data
- learn only relevant factor of variation that keeps data "DATA" perse\
	- every movement in the manifold
- learn vectors of a vector field that points toward the manifold

contractive autoencoder
- sparse + denoising
	- penalize over the variation of $f$ wrt original $x$
	- frobenius norm of the Jacobian
		- that's why is "contractive"