1.  **Foundations of Causality**
    *   Correlation vs. Causation vs. Dependence
	    * X causing Y if a manipulation on X alters the distribution of Y
    *   Reichenbach's Common Cause Principle
	    * [[202603092112|reichenbach theorem]]
		- Common Trends: This isn't Reichenbach's common cause; Coincidental trend over time (a spurious correlation).
		- Selection Bias: If you only collect data from hospitalized people, having a broken leg and having a fever might look correlated, even if they share no causal link in the general population.
		- Small Datasets (Sampling Bias): By pure statistical noise, two variables might look correlated if you don't have enough samples.
		- Measurement Errors & Data Manipulations: Mistakes in how data is collected can artificially create correlations.
2.  **Causal Bayesian Networks**
    *   Definition and Graph Structure
	    * [[202603092131|causal bayesian network]]
    *   Hard Interventions (the $do$-operator)
	    * [[202603092139|do-operator]]
    *   Truncated Factorization of distributions
	    * [[202603092159|truncated factorization]]
3.  **Causal Inference & Effects**
    *   Average Treatment Effect (ATE)
	    * [[202603100847|ATE]]
	* Simpson paradox
		* [[202603100903|Simpson Paradox]]
	*   Causal Effect Identifiability
4.  **Adjustment Criteria**
    *   Causal Sufficiency
    *   Back-Door Adjustment (and Optimal Adjustment sets)
    *   Front-Door Adjustment
    *   Randomized Control Trials (RCTs)
5.  **Structural Causal Models (SCMs)**
    *   Counterfactual Reasoning
    *   SCM Definition and Linear Additive Noise Models (ANM)
    *   Computing Counterfactuals (Abduction, Action, Prediction)
6.  **The Ladder of Causation**
    *   Mapping models (Bayesian Networks $\to$ Causal BNs $\to$ SCMs) to query types (Probabilistic $\to$ Interventional $\to$ Counterfactual)

