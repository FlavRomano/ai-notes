1. **Bayesian Networks (Directed Models)**
   * Joint probability decomposition
   * Fundamental substructures (Tail-to-Tail, Head-to-Tail, Head-to-Head)
	    *   Tail-to-Tail (Common Cause)
			    * [[202603071730|confounder]]
	    *   Head-to-Tail (Causal Chain)
			    * [[202603071742|causal chain]]
	    *   Head-to-Head (Collider/Common Effect)
			    * [[202603071838|collider]]
   * Blocking paths vs. Unlocking paths based on observations ![[Pasted image 20260307183915.png]]
1. **Path Blocking & d-Separation**
   * Conditions for blocked undirected paths
	   * [[202603081557|blocked path definition]]
   * Formal definition of d-separation
	   * [[202603081614|d-separation]]
	   * [[202603081620|example]]
	   * [[202603081710|example analysis]]
1. **Global Markov Property**
   * Equivalence of global and local Markov properties
	   * [[202603081625|global markov property]]
1. **Markov Blanket**
   * Shielding nodes in a Bayesian Network
	   * [[202603081645|markov blanket]]
	   * [[202603081710|markov blanket and global markov property]]
1. **Faithfulness Property**
   * Concisely representing joint distributions 
	   * [[202603081702|faithfulness property]]
	   * [[202603081724|contrast with markov]]
	   * [[202603081733|violation of faithfulness]]
1. **Markov Random Fields (Undirected Models)**
   * Modeling symmetric/bidirectional dependencies
	   * [[markov random fields]]
   * Undirected conditional independence
	   * [[202603081809|node separation in MRF]]
   * Joint probability factorization, Cliques and maximal cliques, Maximal clique factorization 
	   * [[202603081820|joint probability factorization in MRF]]
1. **Converting Directed to Undirected Models**
   * Dealing with v-structures via Moralization ("marrying the parents")
	   * [[202603081845|moralization]]