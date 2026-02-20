1.  **Problem Formulation**
    *   Supervised learning definitions: Regression vs. Classification.
	    * regarding [[202509302141|regression]]
	    * regarding [[202509302227|classification]]
    *   Least Mean Squares (LMS) formulation.
	    * regarding [[202509302152|LMS]]
2.  **Linear Classification**
    *   Geometry of Hyperplanes and decision boundaries.
	    * regarding [[202509302231|decision boundary]]
	    * regarding [[202510011923|scaling freedom property]]
    *   Linear Threshold Units (LTU) and the sign function.
	    * regarding [[202509302240|LTU]]
    *   Adapting regression models (LMS) for classification tasks.
	    * regarding [[202510011925|LMS on classification]]
3.  **Learning Algorithms**
    *   **Direct Approach**: Solving via Normal Equation and SVD (closed-form solution).
	    * regarding [[202510011946|direct approach]]
    *   **Iterative Approach**: Gradient Descent optimization.
	    * regarding [[202510012206|gradient descent]]
    *   Batch vs. On-line (Stochastic) Gradient Descent.
	    * regarding [[202510012210|batch gradient descent]]
	    * regarding [[202510012211|stochastic gradient descent]]
    *   The Delta Rule (error correction learning).
	    * regarding [[202510051043|delta rule]]
4.  **Limitations**
    *   Linearly separable data constraints.
    *   The XOR problem and Language Bias.
	     - regarding [[202602132218|why linearity is a limitation]]
5.  **Model Extensions (Non-linear Modeling)**
    *   **Linear Basis Expansion (LBE)**: Using feature transformation (e.g., polynomials) to model non-linear data while holding the linear learning machinery.
	    * regarding [[202510051202|LBE]]
	    * regarding [[202510051219|curse of dimensionality]]
6.  **Regularization (Complexity Control)**
    *   **Tikhonov Regularization (Ridge Regression)**: Adding a penalty term to the loss function.
	    * regarding [[202510051223|tikhonov]]
	    * regarding [[202510051223|ridge regression]]
    *   Weight decay ($L_2$ norm).
	    * regarding [[202510061801|weight decay]]
    *   Managing the Overfitting/Underfitting trade-off via the Lambda ($\lambda$) hyperparameter.