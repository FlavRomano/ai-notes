1. **Introduction and Recap**
   * Probabilistic and Causal Models (Bayesian Networks, Causal Bayesian Networks, Structural Causal Models)
   * Learning from Structured Data (Parameter vs. Structure Learning)
2. **Fundamentals of Structure Learning**
   * Data Generating Process and Assumptions (Markov Property, Faithfulness, Causal Sufficiency, Acyclicity)
   * Markov Equivalence Classes (MECs) and Partially Completed DAGs (CPDAGs)
   * Overview of Structure Finding Approaches
3. **Constraint-Based Methods**
   * SGS Algorithm (Skeleton, v-structures, and Additional Orientations)
   * Meek Rules
   * PC Algorithm 
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