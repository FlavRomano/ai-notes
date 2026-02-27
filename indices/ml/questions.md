### Learning Theory

- Explain all type of biases.
	  There are basically three main types of biases:
	  - Language bias is an assumption made on the model that shrinks the hypothesis space only to some families of function (by deciding the grade of the polynomials for example);
	  - Search biases is a restriction on the search algorithm that allows to select only some hypothesis over the total space possible with the model;
	  - Inductive bias (or Learning bias) is made by additional assumptions that justify the inductive inference of the model as deductive inferences (e.g. justify the preferred path of search of the model). Inductive Bias can be seen as a mixture of other two biases more than a class for itself.

- How is the Bias-Variance Tradeoff used to decompose generalization error into the model's underlying assumptions versus its sensitivity to training data fluctuations?
	  The formula for the Bias-Variance Theorem is 
	  $E_{P}[(y - h(x))^2] = Bias[h(x)]^2 + Var[h(x)] + \sigma^2$
	  where $\sigma$ is the irreducible noise in the dataset and is inherent to it, instead variance measures how much the model's predictions fluctuate when trained on different, random training sets drawn from the same underlying distribution. It's about sensitivity to the specific training sample, not just the order of the data points.
	  Bias is a systematic error introduced because the model's assumptions (its simplified hypothesis space) fail to capture the true underlying complexity of the data.
	  Usually, when we increment the model complexity the bias shrinks but the variance increase (bigger model, easier to overfit and so to capture noise, the type of data counts more). In the contrary, when the model is simpler it have a bigger bias but it will be less prone to overfitting and to model exactly the seen data. A middle way between them is usually the sweet spot with the best generalization capacity.

- What are the defining characteristics that distinguish a Consistent Learner from an Agnostic Learner in computational learning theory?
	  A Consistent Learner assumes the true target concept belongs to its hypothesis space and therefore actively searches for a hypothesis that achieves exactly zero training error on the dataset. In contrast, an Agnostic Learner makes no prior assumptions about the target concept being present in its hypothesis space; it simply aims to output the hypothesis that minimizes the training error, fully accepting that the lowest achievable error might be greater than zero.

- According to the Fundamental Theorem of Concept Learning, how is the required sample size $N$ bounded by the hypothesis space size $H$ and the error parameter $ϵ$? [non credo ci sia questa roba]
	  According to the Probably Approximately Correct (PAC) learning framework, the minimum number of training examples N required for a consistent learner is bounded by the inequality $N≥ϵ1​(ln∣H∣+ln(δ1​))$. This demonstrates that the required sample size must scale linearly with the inverse of the maximum acceptable generalization error $ϵ$, and logarithmically with both the total size of the hypothesis space $∣H∣$ and the inverse of the failure probability $δ$.

### Validation and Model Selection

- Explain the specific difference between Model Selection and Model Assessment and how the data must be partitioned for each purpose.
	  *Model Selection* is the process of choosing the best model from a set of candidates or tuning the hyperparameters of a specific architecture. The goal is to estimate the performance of different models to pick the winner. This requires partitioning the data into a Training Set (to fit the weights) and a Validation Set (to evaluate hyperparameter performance). If we used the training error for this, we would always pick the most complex, overfitted model.
	  *Model Assessment* is the process of estimating the generalization error of the final, chosen model on new data. Once the best model is selected, we evaluate it one single time on a Test Set. This set must be kept in a "vault" and never used during the selection or training process.

- Describe the K-fold Cross-Validation procedure for model selection and explain how it differs from the Hold-Out method.
	  In the K-fold Cross Validation procedure we try to reduce the variance by dividing the training set (training + validation) in $K$ folds and by training $K$ models (with the same combination of hyperparameters), where in any of them $K-1$ folds are used for training and the remaining fold for validation. After that we estimate the performance of every model by looking at the mean of the performance in every $K$ fold combination, and we then use the best model with a full-retraining on the dull training set and then look at the generalization performance over the test set.

- Why is the Validation Set necessary, and why must it be disjoint from both the Training and Test sets?
	  Validation is used during model selection to estimate the generalization performance of the model, but since is used to change course of the training (by early stopping for example, or more generally we're looking at the best performance on validation so we introduce a bias to obtain the best performance here), we need to have a separate test set for really estimate the generalization performance of the model, a set that cannot be used during the training part but only for the final evaluation.

- What is the difference between an analytical approximation of error (like AIC/BIC) and estimation by resampling (like Bootstrap or Cross-Validation)?
	  Analytical approximations of error, such as AIC, BIC, or Structural Risk Minimization (SRM), estimate generalization performance by summing the empirical training error and a theoretical complexity penalty term, such as one derived from the VC-dimension. This method is computationally efficient because it computes the estimate directly without retraining the model, though it is often limited to specific model classes or provides loose probabilistic bounds. In contrast, estimation by resampling methods like Cross-Validation or Bootstrap approximates the extra-sample error empirically by repeatedly splitting the available data and retraining the model on different subsets. While resampling provides a generally applicable and direct estimate of performance, it is computationally more expensive than analytical methods due to the requirement of multiple training cycles. Both approaches are treated in the course within the section on Validation and Statistical Learning Theory

### Linear Models & K-Nearest Neighbors (K-NN)

- Derive the Normal Equation solution for the Least Mean Squares (LMS) problem in linear models.
	  --- Tablet ---

- Compare the Direct Approach (SVD/Normal Equation) with the **Iterative Approach** (Gradient Descent) for solving linear regression problems.
	  SVD/Normal approach is computationally expensive and using Iterative approaches like Gradient descent where we update the weights based on the error to find the global minimum, remembering that linear models are convex (so there's only one minimum that is the global one). 
	  The weight update is $w_{new} = w - \eta \ \Delta w$ where $\Delta w = \frac{\partial(E_{w})}{\partial(w_{j})}$. This rule of updating the weights proportionally to the error is the *Widrow-Hoff Rule*.

- How the hypothesis space is transformed using a Linear Basis Expansion (LBE) on input?
	  We can send the input in an higher-dimensional space using a Polynomial expansion, where we define $K$ transformation and $\Phi_k(x)$ that contais every transformation to the input $x$, and writing the approximated function $h(x)=\sum_{k} w_{k}\phi_{k}(x) = w^T \phi(x)$.

- Discuss the relationship between the parameter $k$ in K-NN and the flexibility/smoothness of the decision boundary.
	  Higher the $k$, simpler the decision boundary, until the maximum of $k=N$ where every new input is simply a majority vote over all the training data (no need for decision boundary). With higher $k$ so we have more smooth and simpler decision boundary, on the opposite if we reduce $k$ we tends to have more "decision island" around the training points and we tends to overfit giving more importance to noisy points (until the limit of $1$-NN that creates an island over all the training sample, where the VC dimension is infinite).

- Why does the K-NN algorithm suffer from the curse of dimensionality?
	  Because higher the dimensions of the space we're considering for the input, lower the density for the same number of sample. With a lower density the distance between elements of the same class tends to become less important, and in that way it's more difficult to apply $k$-NN that is strongly correlated to use distance to classify new inputs.

### Neural Networks (Advanced & Architectures)

- Explain the differences between Perceptron Learning Algorithm (PLA) and Least Mean Square (LMS) for Neural Networks.
	  Where $d$ is the target, $x$ is the input, PLA use the error $\delta = d - sign(w^Tx)$ simply calculating the sign of the missclassificated examples (the only times update rule is applied) and moving toward the solution.
	  LMS instead update weights every time trying to make the network converge toward the best solution (converge asymptotically) using $\delta = d - w^Tx$.

- Explain the concept of Weight Decay in Neural Networks and its mathematical relationship to Tikhonov regularization.
	  Weight decay is an addition to the loss function $L(w) = E(w) + \lambda \lvert \rvert w \lvert  \rvert$ that tries to limit the "magnitude" of weights (limiting the complexity of the model and the overfitting). The implementation of this with the L2 Norm is often called Tikhonov Regularization or Ridge Regression.
	  The new update rule for Tikhonov Regularization is $w_{new} = w + \eta \ \Delta w - \eta \ 2 \lambda w$.
	  How is obtained in --- Tablet ---. 

- How does the **Universal Approximation Theorem** define the theoretical limits and implications of a feed-forward neural network's ability to represent complex functions?
	  [TODO]

- Why is the **Sigmoid function** preferred over the classic Perceptron's **step function** when considering the requirements of differentiability and the backpropagation algorithm?
	  [TODO]

- What is the mathematical definition of the ReLU (Rectified Linear Unit) activation function, and how do its advantages in gradient propagation compare to the "dying ReLU" disadvantage?
	  [TODO]

- How does the Nesterov Momentum technique improve upon standard Momentum in gradient descent optimization by changing when the gradient is calculated?
	  [TODO]

- Describe the architecture and specific learning mechanisms (constructive approach) of **Cascade Correlation** networks.
	  $\sum_{k} | \sum_{p} (o_{p} - mean(o_{p})) (E_{p,k} - mean(E_{p,k}))|$
	  where p are the patterns and k the outputs of the network (that can have multiple outputs). The mean terms are constant in the formula and are measured over all the patterns for the first term (candidate output term) and over all outputs and patterns for the second term (residual error term). The formula is not used to train the network but to train a "candidate" hidden unit maximize the correlation to the actual error of the network, to try to understand better and solve the actual problems.

- Explain the structure of Convolutional Neural Networks (CNN), specifically the roles of convolutional layers, pooling (subsampling), and weight sharing.
	  In the CNN we can use convolutional layers to extract the salient features from a layer (input or hidden) using a Kernel that accept more inputs at the same time and is connected to a unit of the convolutional layer with the same weight (weight sharing) for every input part we're looking at (like an eye, it has always the same weights and simply analyze the world to send to the brain the results). The rule of the kernel is fixed, the weights of the kernel can be trained.
	  Pooling is a possible approach to down-sampling feature maps by summarizing the presence of features in the inputs part we're analyzing.

- How do local receptive fields, weight sharing, and pooling define the fundamental architectural characteristics of Convolutional Neural Networks (CNNs)?
	  [TODO]

- State Cover’s Theorem and explain how it provides the theoretical justification for Randomized Neural Networks (e.g., Extreme Learning Machines).
	  Cover's Theorem states that non-linearly separable task can easily become a linearly separable one sending it through non-linear features in an higher-dimensional space. That justify RNN because they send the input in an higher dimensional space (like a linear basis expansion) and they only train readout layer to try to solve the task, that maybe in the new space is now linearly separable.

- Discuss the concept of Deep Learning, specifically focusing on representation learning and distributed representations.
	  

- Why is the initialization of weights (e.g., small random values) critical for the Backpropagation algorithm?
	  If weights are _too_ small, the signal diminishes as it passes through many layers. More importantly, in networks using activations like Sigmoid or Tanh, very small weights keep the inputs in the linear region around zero. While this avoids saturation, the resulting gradients can become so tiny after multiple layers (multiplicative effect) that the weights barely update, leading to Vanishing Gradients.
	  If weights are too large, they can cause the weighted sum to be very high. This pushes activation functions (like Sigmoid or Tanh) into their **saturation regions**, where the derivative is nearly zero. This also kills the gradient, stopping learning. Alternatively, in ReLU networks, large weights can cause Exploding Gradients, where updates become so massive that the model becomes unstable and fails to converge.
	  In addition, an initialization to all zeroes leads to the same updates for all the units in the network (every unit will receive the same input and produce the same output, contributing in the same way to the final error and obtaining the same update) does not allow the network to "break the simmetry" and without that all the network is basically a 1 unit network.

- In what ways can the Dropout technique be theoretically connected to ensemble methods like Bagging to improve model generalization?
	  [TODO]

- Can you explain BackPropagation briefly (with formulas)?
	  Formulas on --- Tablet ---

### Support Vector Machines (Hyperparameters & Kernels)

- Explain Mercer's Theorem.
	  Mercer's Theorem provides the theoretical foundation for the Kernel Trick by defining the conditions under which a function can represent an inner product in some high-dimensional feature space. It states that a continuous, symmetric, and positive semi-definite kernel $K(x,x′)$ can be decomposed into an infinite sum of orthogonal basis functions. Specifically, it guarantees that there exists a mapping $ϕ$ such that $K(x,x′)=∑i=1∞​λi​ψi​(x)ψi​(x′)$. In practical terms, this tells us that as long as our kernel matrix is positive semi-definite, we are mathematically "safe" to treat the kernel evaluation as a dot product in a valid Hilbert space, even if we never see that space.

- Explain Cover's Theorem.
	  While Mercer's Theorem explains the "how," Cover's Theorem on the Separability of Patterns explains the "why" behind moving to higher dimensions. It posits that a complex pattern-classification problem is more likely to be linearly separable when cast into a high-dimensional space via a non-linear transformation than it is in a low-dimensional space. Specifically, as the dimensionality of the feature space increases, the probability of finding a hyperplane that perfectly separates different classes approaches 1, provided the transformation is non-linear and the samples are in "general position." This theorem justifies the use of kernels like RBF, as they "lift" data into a space where linear boundaries can solve non-linear problems.

- Explain the Kernel Trick and how it allows linear separation in high-dimensional spaces without explicit transformation.
	  A Kernel function $K(x,z)$ computes the dot product of two vectors in a high-dimensional feature space without ever explicitly performing the transformation $ϕ(x)$. By substituting the standard dot product with this kernel, the model effectively learns a linear decision boundary in the high-dimensional space. 
	  Because this boundary is linear in the higher dimension, it can correspond to a complex, non-linear boundary when mapped back to the original input space. 
	  As Mercer's Theorem says, we can often find a linear solution for non-linear problem in the original dimension.
	  Some examples are RBF (Radial Basis Function) or LBE (Linear Basis Expansion).

- What is the primary difference between Hard Margin and Soft Margin SVMs in terms of how they handle non-linearly separable data and misclassifications?
	  The main difference is that in the soft margin we can allow some misclassifications (regulated by the term $C$, the "cost" of the errors in the function to minimize) and that can allows to find the best hyperplane to separate even non-linearly separable data (the best possible result) ignoring some points that are not classified correctly. 
	  To do so we introduce "slack variables" $ξ$ adding to the function to minimize the term $C \sum^{N}_{p=1}\xi_{p}$. Lower the $C$ term, wider the margin (or more precisely we have less penalty for a misclassification and we can find a wider margin), on the contrary bigger $C$ is, more similar to an hard margin become our Soft-Margin SVM.
	  Hard margin doesn't allows misclassifications, and that lead to the impossibility to find a solution for non-linearly separable problems.
	  We can use kernel trick to bypass the non-linear problem with all the two methods.

- Analyze the effect of the RBF Kernel width ($\gamma$ or $\sigma$) on the complexity (VC dimension) of an SVM model.
	  The formula is $k(v,t​)=e^{−\frac{1}{2\sigma}∣∣v−t​∣∣^2}$.
	  More the value is high, more the elements are correlated, that means that the influence of the parameter $\sigma$ is correlated to how easily two elements can be seen as similar. In particular, lower the $\sigma$ (because of the - sign), more $k(v,t) \rightarrow 0$ and more "isolated island" will be created around points in the hypothesis space, so the model become more complex and tend to overfitting (higher VC-dimension).

- Compare the formulation of Support Vector Regression (SVR) with standard Linear Regression.
	  In the non-linear regression formulation (of the soft margin) we need to consider a $\epsilon$-insensitive tube around the hypothesis function, where the error (the data points that not exactly hit the function) is not considered (on the contrary to margins where data points need to be "pushed out"). We can add two variables $\xi', \xi$ that measures the errors "over the tube", specifically the lower and the upper error. Our model needs to respect the equation:
	  $\xi' - \epsilon \leq d_{p} - w^T\Phi(x_{p}) \leq \xi + \epsilon$
	  We can now rewrite the primal form:
	  Minimize $\Psi(w, \xi', \xi) = \frac{1}{2}w^Tw + C \sum_{p=1}^l \xi' + \xi$

- Discuss the relationship between the hyperparameter $C$ and the margin width (regularization) in Soft Margin SVM.
	  $C$ is the trade-off between maximizing the margin and minimizing the classification error.
	  If we decrease the "cost" $C$ we allow the SVM to do more errors and the margin will usually be larger, given that it doesn't need to adapt in a perfect way to the training data and can be more "simple". In this way we create a model that is less "complex" than an hard margin SVM and that tends to underfitting.
	  On the opposite, increasing $C$ leads to a model that is more and more similar to an hard margin SVM, so less tolerant to errors and that tends to create a more complex separating hyperplane that tends to overfitting.

- What is the advantage of SVM convexity over standard Neural Network training?
	  The main advantages is that we have only a global minimum instead of different local minima that we need to escape to find a better solution, and that solution is independent from the initialization or the training data order. The risk of that is to "overfit" the training data, for that we add the Soft Margin SVM with the cost term $C$, to add the possibility to do some errors, while the problem is still convex.

- How can the Radial Basis Function (RBF) kernel represent an infinite-dimensional feature space, and why don't we run into computational issues (the "curse of dimensionality") when using it?
	  The Radial Basis Function (RBF) kernel represents an infinite-dimensional feature space through its mathematical equivalence to a Taylor series expansion. The kernel is defined by the function $K(x,x′)=exp(−γ∥x−x′∥2)$, and when this exponential term is expanded into its infinite series, it reveals an implicit mapping function, $ϕ(x)$, that contains polynomial terms of every possible degree. Because this power series never terminates, the resulting feature vector effectively resides in a Hilbert space with infinite dimensions.
	  Despite this theoretical infinity, we avoid the "curse of dimensionality" and associated computational meltdowns by utilizing the Kernel Trick. This technique allows us to calculate the inner product of two vectors in that high-dimensional space without ever explicitly defining or storing the coordinates of $ϕ(x)$. Since the SVM or learning algorithm only requires the result of the dot product (a single scalar value), the complexity of the operation depends solely on the number of training samples rather than the dimensionality of the feature space. Thus, we gain the extreme flexibility of an infinite-dimensional model while keeping the computational cost strictly tied to the size of our dataset.

- What are the dual problems of hard and soft margin SVMs? What are the optimal values for dual problems?
	  Given that the primal problems are:
		  - Minimize $\Phi(w) = \frac{1}{2} \lvert\rvert w \lvert\rvert^2_{2}$ constrained by $d_i(w^Tx_{i}+b) \ \geq 1, \forall i=1,\dots,N$
		  - Minimize $\Phi(w, \epsilon) = \frac{1}{2} \lvert\rvert w \lvert\rvert^2_{2} + C \sum_{p=1}^N \epsilon_{p}$ constrained by $d_i(w^Tx_{i}+b) \ \geq 1 - \epsilon$ and $\epsilon_{i} \geq 0,  \forall i=1,\dots,N$
	  The dual problems are:
		  - Maximize $g(\alpha) = \sum_{i=1}^N \alpha_{i} - \frac{1}{2} \sum_{i=1}^N \sum_{j=1}^N \alpha_{i}\alpha_{j}y_{i}y_{j}x_{i}^Tx_{j}$ constrained by $\alpha_{i} \geq 0$ and  $\sum_{i=1}^N \alpha_{i}y_{i} = 0$
		  - Same as above with the change in the first constraint $0 \leq \alpha_{i} \leq C$.

- How can you obtain the dual problems from the primal ones?
	  For obtaining the dual problem we need to do several steps:
	  1. Move the constraints into the optimization problem with the lagrangian terms. By adding this we penalize the objective function if the constraints are violated;
	  2. At this point we need to calculate the minimum of the resulting function with respect to the primal variables. In this way we delete them and we find a concave function that represents the lower bound of the primal problem;
	  3. Finally we need to maximize the resulting function with constraint that all Lagrangian variables needs to be greater or equal than 0.

- Why is important the dual formulation for SVM?
	  In the dual formulation we can see that the inputs $x_i, x_j$ appears only as dot product. We can use that to use Kernel functions to calculate that dot product in an higher-dimensional space.
### Unsupervised Learning & Clustering

- Formulate the Quantization Error function (distortion) and explain how K-means attempts to minimize it.
	  In unsupervised learning we use reference vectors to divide the space in cells called voronoi regions and clusterize the new data based on the distance from these vectors. The Quantization Error $E(w)=\sum_{i}\sum_{j} ||x_{i} - w_{j}||^2 \delta_{winn er}(i,j)$ where $x_i$ is the input, $w_j$ the reference vector and $\delta_{winner}(x,i)$ the function that is equal to $1$ only for the right combination of reference vector and input.
	  K-means try to do a step $\eta$ in the direction of the new input for the chosen reference vector for the on-line version, otherwise create a mean of the inputs for a certain vector in batch version.

- Compare and contrast **K-means** clustering with Self-Organizing Maps (SOM), focusing on the preservation of topological properties.
	  SOM use a fixed maps where every cell has some weights to clusterize the new data. So the new data will be putted inside the right cell and the weight of that cell and of the neighbours will be updated in the direction of the new input, creating after some examples a map where similar inputs will be in the same regions. A distant cell will be less influenced by changes in the chosen cell. The formula for update is:
	  $w_k(t+1) = w_{k}(t) + \eta(t) \ h(winner, k) \ (x - w_{k}(t))$
	  Where $\eta$ changes overtime to decrease the changes after a while, and $h$ is the function that regulate the correlation between reference vectors.

- Explain the Competitive and Cooperative stages in the SOM learning algorithm.
	  Choosing the best unit and then updating the units and neighbours to better classificate

- What is the role of the neighborhood function $h(t)$ in SOM and how does it change over time?
	  The neighborhood function $h$ in SOM decide how much of the update of the "winning" cell for the input needs to be propagated to the neighborhood cells. That helps to create similarity in cells that are close to each others and that function decrease the influence over time to "fine-tune" and "specialize" the cells differences (avoiding to create cells that have nearly the same weights).


### Graph Deep Networks

- Explain a GDN structure.
	  A GNN structure consists of multiple stacked layers that preserve the original graph's topology throughout the network. The input, defined by node features and their adjacency, is processed by repeating a consistent layer architecture where each node’s representation in layer $l+1$ is updated based on its own state and its neighbors' states from layer $l$. This vertical progression through layers is analogous to a time-sequence, but the depth of the network specifically determines the "receptive field," meaning that $L$ stacked layers allow each node to aggregate information from its $L-hop$ neighborhood.

- Explain the Message Passing (MP) mechanism.
	  In the MP mechanism every node of the graph is sending a "message" to all the other neighbour nodes passing its state and changes. In that way every node can be informed about each others to become "aware" of all the topology of the network. the general formula for that is:
	  $h_v^l = AGG_{w_{l}}(L_v, h_{v}^{l-1}), \{h_{u}^{l-1} : u \in N(u)\})$ 

### Generalization & Comparative Questions

- Compare L2 Regularization (Ridge) with L1 Regularization (Lasso) in terms of their effect on the model weights (sparsity vs. shrinkage).
	  L2 adds a penalty to the squared values of the weights and this penalty results in a weight decay that lead to the shrinkage of the weights to smaller values.
	  L1, instead, adds a penalty using the absolute value of the weights and that leads to some weights to become exactly 0, leading to sparsity in the network. That is due to the fact that the derivative of L1 is constant ($\pm 1$ based on the weight sign), L2 depends on the weight force.

- Explain the relationship between Early Stopping in Neural Networks and regularization/VC dimension control.
	  Early Stopping and Regularization try to avoid overfitting and control model comple in different ways. Early Stopping is a form of regularization that checks the validation error and try to stop the training where it sees that the model starts to perform worse on validation data (while perform better on training one).
	  Regularization instead let the model train normally but impose a penalty on weight magnitude, so they can't increase too much, reducing effectively the hypothesis space and the VC-dimension (and if used correctly avoiding noise adaptation).

- Relate the VC dimension to the number of free parameters in a linear model versus a model like 1-Nearest Neighbor.
	  A linear model has a VC-dimension equal to the number of dimensions + 1 ($d+1$) so it's exactly linear in the number of free parameters.
	  The 1-Nearest Neighbor has an infinte VC-dimension (exact model over the training data) and the number of free weights depends on the number of training samples.

- How does increasing the regularization parameter $\lambda$ (lambda) affect the Bias-Variance trade-off?
	  It increase Bias (less complex model that needs to create a bigger bias to fit the training data) and reduce Variance (more difficult to overfit the training data, so the data order count less).

- Discuss the concept of Structural Risk Minimization (SRM) and how it uses the VC dimension to bound the true risk.
	  Given that the True Risk (on the true distribution of data) has an upper limit given by SLT, $R \leq R_{emp} + \epsilon(N,VC,\delta)$ and that inequality gives us the hint that to minimize the true error we need to balance the complexity of the model to minimize the $R_{emp}$ on the data, but also stop at a certain point without using an over-complicated model that will probably capture the noise (overfit) degrading over real-world data performance.

- Compare Neural Networks and SVMs as different forms of Linear Basis Expansion (LBE), specifically focusing on how the basis functions ($\phi$) are determined in each.
	  In NN $\Phi$ is not fixed, but learned through the internal weights. The representation of the space change during the error calculation on the training data, trying to adapt the best "expansion" in the hidden layer to extract the useful features for our task. Every hidden layer in Deep Networks can be seen as an adaptive LBE.
	  In SVM instead the function is fixed, chosen before training, and simply send the input in higher-dimensional space and search the best hyperplane to maximize the margin in this new space and separate the data.
	  A randomized NN can be seen as a fixed linear basis expansion, where you only train the weights that connects the result of the expansion to the output (you simply interpret the $\Phi$ function to minimize the error).
