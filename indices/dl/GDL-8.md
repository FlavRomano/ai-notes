1. **Learning with Incomplete Data**
   * Dealing with 
	   * missing observations 
		   * some variable is observed but data is not complete
	   * and unobserved random variables
		   * we deal with latent variable, like the class within a mixture model
		   * they are not directly observable, like some hidden generative factor

1. **Latent / Hidden Variable Models**
   * Mixture models and discovering natural groupings (no classification)
	   * is a latent variable probabilistic model
	   * each observation is generated from one of $M$ component distribution
	   * the active component is represented by discrete latent variable $Z$
	   * the observed distribution is obtained by marginalizing $Z$
   * Defining joint distributions with latent variables $$P(x,z\mid \theta) = P(x \mid z , \theta) P(z\mid \theta)$$ I get the expectation
   * Computing marginal likelihood (continuous and discrete)
	   * is not feasible, no closed form solution

3. **Maximum Likelihood Learning with Latent Variables**
   * The challenge of computing incomplete likelihood 
	   * with fully observable variable with ML we want to find $$\theta_{ML} = \arg \max_{\theta} \mathcal{L}(\theta \mid X) = \arg \max_{\theta} P(X\mid \theta)$$ parameters that makes the observed data the most probable.
	   * But with latent variable $Z$ that influences directly $X$ we got a big problem, we can't just maximize $P(X\mid \theta)$ because the model requires $Z$ latent. It become an *incomplete likelihood*
   * Formulating the complete likelihood
	   * assuming complete data $d=(X,Z)$ exists
	   * we obtain complete likelihood $$\mathcal{L}_{c}(\theta \mid d)  = P(X,Z\mid \theta) = P(Z\mid X, \theta) P(X \mid \theta)$$
	   * we maximize $\mathcal{L}_{C}$ instead of $\mathcal{L}$

1. **Expectation-Maximization (EM) Algorithm**
	- [[202606101839|Intuition]]
   * E-Step (Expectation) and M-Step (Maximization) 
	   * [[202606101934|E-Step]]
	   * [[202606101950|M-Step]]
   * The assumption we take is that the posterior $P(Z\mid X,\theta)$ is tractable, otherwise we can't do much.
	   * when we have a lot of latent variables

5. **Gaussian Mixture Models (GMM)**
   * Univariate Gaussians and GMM graphical model definition
	   * [[202606111727|learning on univariate gaussians]]
	   * the univariate is the easier case of GMM, because
		   * we observed one variable $x$
		   * we don't have any latent variable
		   * all data comes from the same distribution.
		   * maximum likelihood standard
		*  [[202606111738|Gaussian Mixture Model]]
   * GMM likelihood
	   * [[202606111744|incomplete likelihood in GMM]]
	   * [[202606111838|complete log likelihood]]
	   * [[202606111837|indicator variables]]
   * Applying the EM algorithm to GMMs
