1.  **Learning as an Inference Problem**
    *   Flavors of probabilistic learning: Bayesian, Maximum a-Posteriori (MAP), and Maximum Likelihood (ML)
	    * [[202603061658|Bayesian]]
	    * [[202603061825|Maximum a-posteriori]]
	    * [[202603061845|Maximum Likelihood]]
	    * Finding the parameters $\theta$ of a distribution $P_{\theta}(\cdot)$
		    * or which hypothesis $h_{\theta}$ to use (inference problem formulation)
    *   Considerations on Bayesian Learning and Prior Regularization (penalizing complexity)
	    * [[202606091633|tractability issues]]
	    * ML and MAP are **point estimates** of the Bayesian, they infer based only on one most likely hypothesis $h_{\theta_{MAP}}$ pr $h_{\theta_{ML}}$
	    * [[202606091643|MAP prior regularization]]
2.  **Learning with Graphical Models**
    *   Categorization of learning problems (Parameter vs. Structure learning)
	    * parameter learning
		    * fixed structure
		    * only parameter estimation
		* structure learning
			* structure itself should be discovered
    *   Complete vs. Incomplete data scenarios 
	    * complete
		    * every variable is observed
		    * for every sample we know the value of each variable
		* incomplete
			* some variables in the model are not observed
			* latent variables, the model must infer missing information while learning.
3.  **Parameter Learning with Fully Observable Models**
    *   Maximum-Likelihood Estimation (MLE) and Log-Likelihood optimization
	    * [[202606091712|MLE]]
	    * [[202606091754|ML vs MAP]]
	    * after computing the log-likelihood, we choose the parameter with the highest likelihood
    *   Example: The Biased Coin with MLE (entirely data-driven)
    *   MAP Estimation and Conjugate Distributions (e.g., Beta prior for the Biased Coin)
    *   The Bayesian Approach (learning a distribution over models using the whole posterior)
4. **The Naïve Bayes Classifier**
	- [[202606091806|Intuition]]
    *   [[202606101553|The Naïve Bayes Assumption]](Conditional independence between attributes)
    * [[202606101555|model parameters]]
    *   [[202606101616|Formulating the Naïve Bayes Likelihood]](using indicator variables)
    *   [[202606101700|Addressing scarce data with Prior Estimates]] (Laplacian smoothing / virtual counts)
