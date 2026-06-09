Section 6 is where the paper validates the entire GRAND framework experimentally.

Up to this point, the paper developed:

- the PDE interpretation,
    
- the diffusion equations,
    
- the numerical solvers,
    
- the GRAND architectures.
    

Now the authors ask:

> “Does this actually improve graph learning in practice?”

This section tries to answer four major questions:

1. Are diffusion-based GNNs competitive?
    
2. Can GRAND build deeper GNNs?
    
3. Do implicit methods really help?
    
4. Does rewiring improve diffusion?
    

The section is structured around these questions.

---

# The Big Experimental Philosophy

The authors are not only testing:

- “Does GRAND get good accuracy?”
    

They are testing the entire PDE viewpoint:

> Does numerical analysis actually matter for GNN design?

This is very important.

The experiments are designed to validate:

- stability theory,
    
- solver choices,
    
- diffusion interpretations,
    
- rewiring,
    
- continuous-time dynamics.
    

---

# Section 6.1 — Node Classification Benchmarks

This subsection answers:

> “Can GRAND compete with standard GNNs on real datasets?”

This is the main benchmark evaluation.

---

# 1. Experimental Goal

The paper wants to compare:

## Standard GNNs

- GCN
    
- GAT
    
- GraphSAGE
    
- MoNet
    

against:

## Continuous / ODE-based GNNs

- CGNN
    
- GDE
    
- GODE
    

and finally:

## GRAND variants

- GRAND-l
    
- GRAND-nl
    
- GRAND-nl-rw
    

---

# 2. The Three GRAND Variants

Understanding these is crucial.

---

## GRAND-l (Linear)

Attention matrix fixed during diffusion:

[  
A(X(t)) = A  
]

So:

- linear diffusion,
    
- simpler dynamics,
    
- analytical interpretation.
    

---

## GRAND-nl (Nonlinear)

Attention changes during evolution:

[  
A=A(X)  
]

Now diffusion becomes:

- adaptive,
    
- feature-dependent,
    
- nonlinear.
    

---

## GRAND-nl-rw (Nonlinear + Rewiring)

Adds:

- graph rewiring,
    
- dynamic connectivity.
    

This improves:

- long-range propagation,
    
- bottleneck reduction,
    
- global communication.
    

---

# 3. Datasets Used

The paper evaluates on standard node classification benchmarks:

|Dataset|Type|
|---|---|
|Cora|Citation network|
|CiteSeer|Citation network|
|PubMed|Citation network|
|CoauthorCS|Coauthor graph|
|Amazon Computer|Co-purchase graph|
|Amazon Photo|Co-purchase graph|
|ogbn-arxiv|Large citation graph|

---

# Why These Datasets Matter

These are the classical benchmarks for GNNs.

Using them allows:

- direct comparison with prior work,
    
- validation against strong baselines.
    

---

# 4. Important Experimental Detail

The paper criticizes earlier evaluation practices.

Historically:

- many papers used only one train/test split,
    
- results were noisy and unreliable.
    

So GRAND uses:

- 100 random splits,
    
- 20 random initializations.
    

This is very important scientifically.

---

# Why This Matters

GNN performance can vary significantly depending on:

- initialization,
    
- train/test split,
    
- randomness.
    

Using many splits:

- makes evaluation statistically reliable.
    

---

# 5. Hyperparameter Search

The authors use:

- large-scale random search,
    
- asynchronous hyperband scheduling.
    

This means:

- GRAND was carefully tuned,
    
- comparisons are fair.
    

---

# 6. Numerical Solver Choices

This part is subtle but important.

Different datasets use different numerical solvers:

|Dataset Size|Solver|
|---|---|
|Small datasets|Dormand–Prince|
|ogbn-arxiv|Runge-Kutta|

---

# Why Different Solvers?

Because:

- different graphs produce different dynamics,
    
- adaptive solvers are expensive on huge graphs.
    

This reinforces the paper’s core idea:

> solver choice matters in GNNs.

---

# 7. Regularization

The paper uses:

- kinetic energy regularization,
    
- Jacobian regularization.
    

These techniques encourage:

- smooth dynamics,
    
- easier numerical integration,
    
- stable ODE trajectories.
    

---

# Why This is Important

Neural ODE systems can become:

- stiff,
    
- chaotic,
    
- difficult to solve numerically.
    

Regularization keeps the diffusion:

- smooth,
    
- well-conditioned.
    

This directly connects to Section 3.2 stability theory.

---

# 8. Complexity Analysis

The paper analyzes:

- memory complexity,
    
- runtime complexity.
    

The dominant cost comes from:

- evaluating attention over edges.
    

Complexity:

[  
O(|E'|d)  
]

where:

- (E') = rewired edges,
    
- (d) = feature dimension.
    

---

# Important Insight

Runtime depends on:

- number of solver evaluations.
    

Unlike standard GNNs:

- depth is dynamic.
    

So:

- computational cost depends on solver behavior.
    

This is very different from classical architectures.

---

# 9. Parameter Efficiency

One of the strongest practical results.

Traditional GNNs:

- add parameters per layer.
    

GRAND:

- shares parameters across diffusion time.
    

The paper states:

|Model|Parameters|
|---|---|
|GCN|143K|
|GraphSAGE|219K|
|GAT|1.63M|
|GRAND|70K|

---

# Why GRAND Uses Fewer Parameters

Because:

- the same diffusion operator evolves continuously,
    
- no separate layer parameters needed.
    

This is one of the biggest advantages of continuous-time models.

---

# 10. Main Results — Table 1

Table 1 evaluates:

- Planetoid fixed splits.
    

GRAND performs:

- first place or near first place on almost all datasets.
    

---

# Important Observation

The strongest result is not necessarily:

- raw accuracy.
    

The real achievement is:

> achieving comparable or better performance with dramatically fewer parameters and better stability.

This is the key scientific contribution.

---

# 11. Random Split Results — Table 2

Table 2 is even more important.

It evaluates:

- many random train/test splits.
    

GRAND remains among the best methods across datasets.

---

# Why This is Significant

It shows:

- GRAND is robust,
    
- not overfit to benchmark splits,
    
- generalizes well.
    

This is strong evidence that:

- the diffusion formulation is meaningful.
    

---

# 12. The Most Important Scientific Conclusion

Section 6.1 validates the paper’s central thesis:

> Better numerical diffusion methods lead to better graph neural networks.

Specifically:

- continuous diffusion works,
    
- adaptive dynamics work,
    
- parameter sharing works,
    
- PDE-inspired architectures are competitive.
    

---

# 13. The Hidden Deeper Message

The experiments are actually proving something larger:

Traditional GNN design:

- largely empirical.
    

GRAND shows:

- numerical analysis principles predict performance improvements.
    

This is the real conceptual breakthrough.