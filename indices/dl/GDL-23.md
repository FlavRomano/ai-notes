Generative models try to characterize data distribution
- understand the data
- understand the [[factors of variation]]
- understand normality

Generative learning is [[similar to unsupervised learning]]. This similarity led to [[foundation model paradigm]].

We got training data $X$. The data distribution $P(x)$ is unknown but...
- we can use an approximation $\sim P(x)$
- from which generate new $\sim P_{\theta}(x)$
	- learning taxonomy
		- [[explicit]]
			- [[visible]]
			- [[latent]]
				- [[variational]]
				- [[stochastic]]
		- [[implicit]]
			- [[direct]]
			- [[stochastic]]

![[Drawing 2026-05-09 17.01.09.excalidraw]]

The autoencoder is a model trained to reconstruct its input

![[Pasted image 20260509170702.png]]

The core is in the [[information bottleneck]] ($K \ll D$).

The loss of unsupervised task is [[reconstruction error minimization]].

We have different types of neural autoencoders:
- regularized ones
	- [[202605091716|sparse AE]]
	- [[202605091723|denoising AE]]
	- [[contractive AE]]
- AE with [[dropout layers]]


