# Attention use and its meaning (diffusivity)
GRAND interprets graph attention as a learnable diffusivity operator inside a continuous graph diffusion equation.

The attention matrix controls how strongly information propagates between nodes, defining the graph diffusion geometry. Using scaled dot-product attention, GRAND learns adaptive and anisotropic diffusion dynamics based on node similarity:

$$a(X_i,X_j)=\text{softmax}\left(\frac{(W_KX_i)^TW_QX_j}{d_k}\right)$$

# Parameters sharing and discretizing
In GRAND, parameter sharing means that the same diffusion operator and learnable parameters are reused across all discretization steps of the continuous diffusion process.

$$\frac{dX}{dt}=f(X,t,\theta)$$

Unlike traditional GNNs, where each layer has independent weights, GRAND generates all effective layers from the same underlying dynamics. This greatly reduces the number of parameters while promoting stable and coherent feature evolution across depth.

## note 
- shorter

# Backpropagation and Pontryagin

| **Optimization Method**            | **Time Complexity (Forward + Backward)** | **Memory Complexity (Space)** | **Scaling Bottleneck**                        |
| ---------------------------------- | ---------------------------------------- | ----------------------------- | --------------------------------------------- |
| **1. Direct Backpropagation**      | $\mathcal{O}(N \cdot K)$                 | $\mathcal{O}(N \cdot K)$      | **Memory-bounded** (Scales with solver steps) |
| **2. Pontryagin / Adjoint Method** | $\mathcal{O}(N \cdot (K_f + K_b))$       | $\mathcal{O}(N)$              | **Time-bounded** (Requires a second ODE pass) |

# Merged
**Graph Neural Diffusion (GRAND)** is a family of GNN architectures in which, given node features  and a graph , input features are encoded into initial embeddings, then instead of applying  a fixed stack of GNN layers, it evolves node embeddings through a continuous graph diffusion process. 
A numerical ODE solver integrates these dynamics from $t = 0$ to $t=T$, producing the final embeddings $X(T)$, which are then processed by a decoder to obtain node predictions.  
A central contribution of GRAND is the interpretation of graph attention as a learnable diffusivity operator inside the diffusion equation. The attention matrix controls how strongly information propagates between nodes, defining the geometry of diffusion on the graph. Using scaled dot-product attention, GRAND learns adaptive and anisotropic diffusion dynamics based on node similarity:
$$a(X_i,X_j)=\text{softmax}\left(\frac{(W_KX_i)^TW_QX_j}{d_k}\right)$$ GRAND shares the same diffusion operator and learnable parameters across all discretization steps of the continuous process. This parameter sharing significantly reduces the number of parameters while promoting stable and coherent feature evolution across depth.
Another key aspect of GRAND is that the choice of the numerical solver determines how the continuous diffusion process is discretized. Furthermore, in GRAND, the choice of the numerical solver determines how the continuous diffusion is discretized. Therefore, choosing a solver becomes an important part of the GNN architecture design, as it contributes to stability. **Explicit** schemes, such as Euler, are simple and resemble residual message-passing  updates, but they are stable only for sufficiently small step sizes. **Multi-step** and Runge–Kutta schemes improve the approximation of the diffusion trajectory by evaluating the  
dynamics at multiple points, rather than using only the current state. This  
allows the solver to follow the continuous evolution of node embeddings  
more accurately from  to , reducing the error introduced by  
discretizing the diffusion process. **Implicit** schemes are computationally more expensive because they require solving an equation  at each step, but  
they provide stronger stability guarantees. Training in GRAND is performed end-to-end through the continuous diffusion solver. Gradients can be computed either by direct backpropagation through all solver steps or using adjoint methods based on Pontryagin’s Maximum Principle.

| Optimization Method         | Time Complexity                | Memory Complexity       | Main Limitation |
| --------------------------- | ------------------------------ | ----------------------- | --------------- |
| Direct Backpropagation      | $$(\mathcal{O}(N\cdot K))   $$     | $$\mathcal{O}(N\cdot K)$$ | Memory-bounded  |
| Pontryagin / Adjoint Method | $$(\mathcal{O}(N\cdot(K_f+K_b)))$$ | $$\mathcal{O}(N)$$        | Time-bounded    |