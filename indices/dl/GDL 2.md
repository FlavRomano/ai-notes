1.  **Probabilistic and Graphical Models**
    *   Role of probabilistic models in Generative Deep Learning.
    *   The Graphical Models framework: Representation, Inference, and Learning.
    *   Graph types: Directed (Causal), Undirected (Soft constraints), and Dynamic.

2.  **Probability Theory Refresher**
	- [[202602201842|Marginal definition and marginalisation]]
    *   Random Variables (Discrete vs. Continuous).
    *   Joint and [[202602201848|Conditional probabilities]].
    *   Key Theorems: Chain Rule (Product Rule), Marginalization (Sum Rule), and Bayes Rule.
    *   [[202602201914|Variable independence]] and Conditional Independence ($X \perp Y \mid Z$).
    *   Expectation (Definitions and linear properties).

3.  **Probability Distributions**
    *   Discrete domains: Bernoulli and Categorical distributions.
    *   Continuous domains: Gaussian (Univariate/Multivariate), Beta, and Dirichlet distributions.
    *   **Conjugate Priors**: Matching priors with likelihoods to ensure closed-form posteriors.

4.  **Inference and Learning**
    *   Framing "Learning" as a specific type of Inference problem.
    *   **Bayesian Inference**: Weighing all hypotheses by probability (Optimal but computationally expensive).
    *   **Maximum A Posteriori (MAP)**: Selecting the single most likely hypothesis given the data.
    *   **Maximum Likelihood (ML)**: Selecting the hypothesis that maximizes data probability (assuming uniform priors).

5.  **Case Study: The Candy Box Problem**
    *   Applying Bayesian updating to sequential observations.
    *   Visualizing how hypothesis posteriors evolve and converge as data increases.