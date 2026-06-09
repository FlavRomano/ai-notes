1. **Introduction and Recap**
   * Probabilistic and Causal Models (Bayesian Networks, Causal Bayesian Networks, Structural Causal Models)
   * Learning from Structured Data (Parameter vs. Structure Learning)
	   * from data to structure
	   * we got data but don't know how to connect them in a BN for example
1. **Fundamentals of Structure Learning**
   * Data Generating Process and Assumptions (Markov Property, Faithfulness, Causal Sufficiency, Acyclicity)
   * Markov Equivalence Classes (MECs) and Partially Completed DAGs (CPDAGs)
	   * [[202606091158|markov equivalence class]]
   * Overview of Structure Finding Approaches
1. **Constraint-Based Methods**
   - possible strictly due to Causal Sufficiency assumption (not real world)
   * SGS Algorithm (Skeleton, v-structures, and Additional Orientations)
	   * [[202606091207|SGS]]
   * Meek Rules
		* 4 rules to encode information in the skeleton
		* [[202606091238|meek rules]]
			- [[202606091527|R1]]
			- [[202606091532|R2]]
			- [[202606091537|R3]]
			- [[202606091557|R4]]
   * PC Algorithm 
	   * instead of checking all possible separating sets (as in SGS)
	   * PC considers separating sets of increasing size
	   * same worst case of SGS but much better on average
   * Testing Strategies (Level-wise vs. Node-wise)
4. **Search and Score-Based Methods**
   * Scoring Functions (Properties, Information Theoretic vs. Bayesian, Bayesian Information Criterion - BIC)
   * Search Strategies (Local operations, Cost optimization)
   * GES Algorithm (Greedy Equivalence Search via Insertion, Deletion, Reversal)
5. **Hybrid Models**
   * Combining constraint and score-based approaches 
   * Max-Min Hill Climbing (MMHC)
6. **Parametric Identifiability and Conclusions**
   * Limits of Structure Learning (Why algorithms often only return the MEC)
   * Identifiability Results for Structural Causal Models (SCMs)
   * Take Home Messages (Importance of assumptions and prior knowledge)