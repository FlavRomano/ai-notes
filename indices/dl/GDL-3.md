1.  **Representing Joint Distributions**
    *   Goals of probabilistic modeling (Sampling, Inference, Likelihood)
    *   The Chain Rule and directed graphs
	    * [[202603071630|chain rule]]
    *   Parameter complexity ($k^N - 1$) vs. reduction via independence
	    * [[202603071635|parameter complexity]]
	    * [[202602201914|variable independence]]
		    * we only need $nk$ parameters

2.  **Independence Concepts**
    *   Marginal Independence definition
    *   Conditional Independence definition
	    * [[202602211112|conditional independence]]

3.  **Bayesian Networks (BNs)**
    *   Discrete BNs and Conditional Probability Tables (CPTs)
	    * [[202603071643|bayesian networks]]
	    * [[202603071648|CPT]]

4.  **Compact Representation**
    *   Plate Notation for replicated dependencies ![[Pasted image 20260307165431.png]]
    *   Distinction between observed (shaded) and latent (empty) variables ![[Pasted image 20260307165457.png]]
	    * shaded = observed
	    * empty = hidden
	    * black seeds = model parameters

5.  **Properties and Operations**
    *   The Local Markov Property
	    * [[202603071701|local markov property]]
    *   Joint Probability Factorization (Topological ordering) by applying chain rule and local markov property
	    * [[202603071712|joint probability factorization]]
    *   Ancestral Sampling (Generative process)

6.  **Fundamental BN Structures & Flow**
    *   Tail-to-Tail (Common Cause)
	    * [[202603071730|confounder]]
    *   Head-to-Tail (Causal Chain)
	    * [[202603071742|causal chain]]
    *   Head-to-Head (Collider/Common Effect)
    *   Blocking paths vs. Unlocking paths based on observations