1.  **Learning as an Inference Problem**
    *   Flavors of probabilistic learning: Bayesian, Maximum a-Posteriori (MAP), and Maximum Likelihood (ML)
    *   Considerations on Bayesian Learning and Prior Regularization (penalizing complexity)
2.  **Learning with Graphical Models**
    *   Categorization of learning problems (Parameter vs. Structure learning)
    *   Complete vs. Incomplete data scenarios 
3.  **Parameter Learning with Fully Observable Models**
    *   Maximum-Likelihood Estimation (MLE) and Log-Likelihood optimization
    *   Example: The Biased Coin with MLE (entirely data-driven)
    *   MAP Estimation and Conjugate Distributions (e.g., Beta prior for the Biased Coin)
    *   The Bayesian Approach (learning a distribution over models using the whole posterior)
4. **The Naïve Bayes Classifier**
    *   The Naïve Bayes Assumption (Conditional independence between attributes)
    *   Formulating the Naïve Bayes Likelihood (using indicator variables)
    *   Maximization of the Naïve Bayes Log-Likelihood
    *   Addressing scarce data with Prior Estimates (Laplacian smoothing / virtual counts)