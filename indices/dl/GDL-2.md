1.  **Probabilistic and Graphical Models**
    *   Role of probabilistic models in Generative Deep Learning.
    *   The Graphical Models framework: Representation, Inference, and Learning.
    *   Graph types: Directed (Causal), Undirected (Soft constraints), and Dynamic.

2.  **Probability Theory Refresher**
    *   Random Variables (Discrete vs. Continuous).
    *   Joint and Conditional probabilities.
	    * [[202603061740|joint distribution]]
	    * [[202602201848|Conditional probabilities]].
    *   Key Theorems: Chain Rule (Product Rule), Marginalization (Sum Rule), and Bayes Rule.
    	- [[202602201842|Marginal definition and marginalization]]
	    * [[202603061733|product rule]]
	    * [[202603061701|bayes rule]]
	    * [[|marginal likelihood]]
    *   [[202602201914|Variable independence]] and [[202602211112|Conditional Independence]] ($X \perp Y \mid Z$).
    *   Expectation (Definitions and linear properties).

3.  **Probability Distributions**
    *   Discrete domains: Bernoulli and Categorical distributions.
    *   Continuous domains: Gaussian (Univariate/Multivariate), Beta, and Dirichlet distributions.
    *   **Conjugate Priors**: Matching priors with likelihoods to ensure closed-form posteriors.

4.  **Inference and Learning**
	- We want to predict a variable $X$ after seeing $d$ data and considering the hypothesis space $H$
    *   **Bayesian Inference**: Weighing all hypotheses by probability (Optimal but computationally expensive).
	    * [[202603061658|bayesian prediction]]
    *   **Maximum A Posteriori (MAP)**: Selecting the single most likely hypothesis given the data.
	    * [[202603061825|MAP]]
    *   **Maximum Likelihood (ML)**: Selecting the hypothesis that maximizes data probability (assuming uniform priors).
	    * [[202603061845|ML]]
	* Confrontation

5.  **Case Study: The Candy Box Problem**
    *   Applying Bayesian updating to sequential observations.
    *   Visualizing how hypothesis posteriors evolve and converge as data increases.