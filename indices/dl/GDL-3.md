1.  **Representing Joint Distributions**
    *   Goals of probabilistic modeling (Sampling, Inference, Likelihood)
    *   The Chain Rule and directed graphs
    *   Parameter complexity ($k^N - 1$) vs. reduction via independence

2.  **Independence Concepts**
    *   Marginal Independence definition
    *   Conditional Independence definition

3.  **Bayesian Networks (BNs)**
    *   Definition: Directed Acyclic Graphs (DAGs)
    *   Nodes (variables) and Edges (conditional independence)
    *   Discrete BNs and Conditional Probability Tables (CPTs)
    *   Statistical dependence vs. Causality

4.  **Compact Representation**
    *   Plate Notation for replicated dependencies
    *   Distinction between observed (shaded) and latent (empty) variables

5.  **Properties and Operations**
    *   The Local Markov Property
    *   Joint Probability Factorization (Topological ordering)
    *   Ancestral Sampling (Generative process)

6.  **Fundamental BN Structures & Flow**
    *   Tail-to-Tail (Common Cause)
    *   Head-to-Tail (Causal Chain)
    *   Head-to-Head (Collider/Common Effect)
    *   Blocking paths vs. Unlocking paths based on observations