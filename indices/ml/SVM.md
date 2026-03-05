1.  **Foundations of Linear SVM**
    *   Linearly separable patterns and the separating hyperplane.
    *   The concept of the Separation Margin and the "safe zone."
    *   Goal: Maximizing the margin ($\rho$) equivalent to minimizing the weight norm ($||w||$).
    *   Structural Risk Minimization vs. Empirical Risk Minimization.

2.  **Hard Margin Optimization**
    *   Canonical representation and definition of Support Vectors.
    *   **The Primal Problem:** Quadratic optimization to minimize $||w||$ subject to classification constraints.
    *   **Lagrangian Formulation:** Converting the problem using Lagrangian multipliers.
    *   **Kuhn-Tucker Conditions:** Defining the optimal solution boundaries.
    *   **The Dual Problem:** Maximizing based on dot products; solution depends only on Support Vectors.
    *   Theoretical justification: Vapnik’s Theorem and controlling VC dimension.

3.  **Soft Margin SVM (Handling Noise)**
    *   Addressing non-linearly separable data and outliers.
    *   Introduction of **Slack Variables** ($\xi$) to allow margin violations.
    *   The **Regularization Parameter ($C$):** Trade-off between margin width and training error.
    *   Modified constraints ($0 \le \alpha_i \le C$) in the Dual problem.

4.  **Kernel Methods (Non-Linear Classification)**
    *   Mapping inputs to a high-dimensional Feature Space ($\Phi$).
    *   **The Kernel Trick:** Computing dot products in feature space ($k(x, y)$) without explicit mapping.
    *   Mercer’s Theorem and conditions for valid kernels (semi-definite positive matrices).
    *   Common Kernels: Polynomial, Radial Basis Function (RBF/Gaussian), and Sigmoid.

5.  **SVM for Regression (SVR)**
    *   Adapting SVM to predict continuous values.
    *   **$\epsilon$-Insensitive Loss Function:** Ignoring errors within a specific threshold.
    *   The concept of the **$\epsilon$-tube** around the regression line.
    *   Optimization formulation (Primal and Dual) using slack variables for regression.

---

1.  **SVM Characteristics and Trade-offs**
    *   **Pros:** Convex optimization (global minimum), built-in regularization, and theoretical bounds (SRM).
    *   **Cons:** Computational cost on massive datasets (batch algorithm) and sensitivity to kernel choice.
    *   **Historical Context:** Success on MNIST handwritten digits (comparable to CNNs in the late 90s).

2.  **Practical Tuning and Model Selection**
    *   **Kernel Comparison:** Visualizing decision boundaries (Polynomial vs. RBF).
    *   **Hyper-parameter Interaction:** The critical relationship between Regularization ($C$) and Kernel width ($\sigma$ or $\gamma$).
    *   **Controlling Complexity:** How small RBF widths can lead to overfitting (infinite VC-dimension) vs. large widths acting as global averages.
    *   **Validation:** Necessity of Cross-Validation for selecting $C$ and kernel parameters.

3.  **SVM "Folklore" (Common Misconceptions)**
    *   Addressing myths regarding default parameters and immunity to overfitting.
    *   Clarification on the "Curse of Dimensionality": SVM handles high dimensions in *feature* space, but does not solve high dimensionality in *input* space.

4.  **Beyond SVM: General Kernel Methods**
    *   **"Kernelization":** Applying the Kernel Trick to any algorithm using dot products (separating the solver from the data representation).
    *   **Modularity:** The ability to change the kernel matrix ($K$) without changing the learning algorithm.
    *   **Similarity Measures:** Interpreting Kernels as pairwise comparisons ($k(s,t)$) rather than explicit feature extraction.
    *   **Structured Data:** Designing Kernels for non-vector inputs (graphs, strings, trees) and domain-specific tasks.