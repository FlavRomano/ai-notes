unsupervised disentanglement
- beta vae
	- posterior and prior are not the same
	- that's why beta vae is not good, factorVAE is preferred
- factorVAE
	- now we minimize total correlation (element wise)
	- regularized KL divergence

latent trasversal 
- like interventions in causality
- cannot disambiguate with unsupervised disentanglement
	- weak supervision signal is preferred

weak supervised disentanglement
- context/regime variable
	- distributions changes across the context/regime
	- gdp-instruction example
- iVAE
	- KL divergence now with $u$
		- in particular we don't have anymore the prior, but the conditional probability
	- the trick is similar to conditional auto encoders
		- the condition $u$ is inputed to the encoder

TRIS
- dataset of triplets (TRIS)
- we don't now the causal relations but we now the intervantion applied to a causal relation
