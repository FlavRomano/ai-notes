1. **Problem Setup & Introduction**
   * Intractable latent variable models and maximum likelihood challenges
   * Meaning of the "Variational" term (Calculus vs. Variational Calculus)
   * Tractability issues in Bayesian learning and the Expectation-Maximization (EM) algorithm

2. **Fundamental Mathematical Tools**
   * **Kullback-Leibler (KL) Divergence:** An information-theoretic measure of closeness between two distributions
   * **Jensen's Inequality:** Properties of linear operators on convex/concave functions applied to a probabilistic setting

3. **Bounding the Likelihood**
   * The bound maximization view of the EM algorithm
   * Generalizing lower bound maximization using a tractable family of distributions ($Q$)

4. **The Evidence Lower Bound (ELBO)**
   * Bounding the log-likelihood using Jensen's Inequality to derive the ELBO
   * Evaluating the tightness of the lower bound using marginalization and KL Divergence
   * The fundamental equation: $\log P(x|\theta) = \text{ELBO} + \text{KL Divergence}$

5. **Variational Inference & Optimization**
   * Framing variational inference as an alternative optimization problem
   * Two flavors of variational inference: EM maximizing the bound vs. minimizing the KL divergence
   * The reformulated variational view of Expectation-Maximization (solving a double optimization problem)