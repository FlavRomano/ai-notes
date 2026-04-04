1. **Introduction to Latent Topic Models**
   * Latent Variable Models for high-dimensional data
   * Probabilistic representation (Bag-of-Words & Multinomial data)
   * Core concept: Single-topic vs. Mixed-topic document membership

2. **The Latent Dirichlet Allocation (LDA) Model**
   * Plate notation and model distributions ($\alpha, \theta, z, w, \beta$)
   * The Dirichlet prior and its geometric interpretation (The Simplex)
   * Controlling sparsity: The effect of the $\alpha$ hyperparameter 
   * Step-by-step generative process of a document

3. **Learning & Inference in LDA**
   * Marginal likelihood and Expectation-Maximization (EM)
   * The core problem: Intractability of the exact latent variable posterior
   * The solution: Variational Expectation-Maximization
   * The Mean-Field approximation (factorizing the dependencies) and the ELBO

4. **The LDA Learning Algorithm (Math & Pseudocode)**
   * E-Step: Approximating the document-specific parameters (topic proportions and responsibilities)
   * M-Step: Maximizing the global parameters (topic-word counts)
   * Iterative training pseudocode 

5. **Applications & Extensions**
   * Non-text applications: Image understanding via "Visual Words"
   * Dynamical Topic Models: Tracking topic evolution over time
   * Software libraries for variational learning (PyMC3, Edward, Gensim, etc.)