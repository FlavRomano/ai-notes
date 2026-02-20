1.  **General Training Issues**
    *   The problem of non-convex optimization and local minima.
    *   Importance of weight initialization (e.g., symmetry breaking, Fan-in).
    *   Global minima vs. generalization capability.

2.  **Gradient Descent Variants**
    *   **Batch:** Calculating gradients over the entire dataset.
    *   **On-line (Stochastic - SGD):** Updating weights per pattern; "Zig-zag" descent.
    *   **Mini-batch:** Updating weights after a subset of patterns.

3.  **Optimization Improvements**
    *   **Learning Rate ($\eta$):** Heuristics, Least Mean Square (LMS) scaling, and learning curves.
    *   **Momentum:** Standard Momentum and Nesterov Momentum to speed up convergence.
    *   **Advanced Techniques:** Variable learning rates, Adaptive rates (AdaGrad, Adam), and Second-order methods (Hessian matrix, Saddle points).

4.  **Stopping Criteria & Complexity Control**
    *   Heuristics for stopping (error thresholds, gradient changes).
    *   **Overfitting:** The relationship between training steps, VC-dimension, and generalization.
    *   **Regularization:** Implementing Weight Decay (Tikhonov), penalty terms, and the distinction between Error and Loss.

5.  **Network Architecture**
    *   Selecting the number of hidden units (Model Selection).
    *   **Constructive Approaches:** Algorithms that build topology during training.
    *   **Cascade Correlation (CC):** Architecture evolution and correlation maximization learning.

6.  **Input/Output Representation**
    *   **Preprocessing:** Standardization and scaling.
    *   **Encodings:** 1-of-K (One-hot) encoding for categorical data.
    *   **Output Units:** Linear (Regression) vs. Sigmoid/Softmax (Classification) and Cross-Entropy loss.

7.  **Conclusion**
    *   Historical timeline of Neural Networks.
    *   Summary of advantages (universality, flexibility) and disadvantages (black-box nature, architectural tuning).