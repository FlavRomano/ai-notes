assumption on data
- realization of the model
- is possible to go from data to structure?
	- is undefined
	- structure learning algorithm

Injection of assumptions on algorithm implies from data to graph.

Markov Equivalence Class (MEC)
- set of graphs with similiar properties
	- are DAGs
	- and have the same skeleton
		- skeleton=DAG with undirected edges
	- and have the same colliders
		- remark: colliders can only be colliders
	- then they represent the same MEC

Constraint-Based Methods
- strictly due to Causal Sufficiency
	- not a real world assumption

SGS Algorithm
- skeleton
	- start from fully connected undirected graph first
	- then cut edges to find the skeleton
		- pruning line in the code
		- pick an edge, then find all the possible subset of the graph without that edge
		- for each subset candidate
			- try to prove edge marginally independence given the subset
			- find the separating set, which variable should I block to separate the two node of the edge (markov property)
		- cut the edge if marginally independent
- no separating set without X and Y
- then identify the collaiders
	- X and Y not adjecent in the skeleton
	- But a third variable W 
		- adjecent to X and Y
		- W is not a member of any separating set
			- so X and Y are independent in each separating set W-less
	- then we have a collider
- we find ALL the graph inside a MEC
	- the undirected edged possible graph
		- confounder, etc... but never colliders
		- we would found it previously

Meek rules
- 4 rules to encode information in the skeleton
- useful to avoid the creation of
	- new cycles
	- new colliders

PC
- algorithm use an heuristic to do the same thing of SGS but faster

Bayesian information Criterion score
- likelihood of the Dataset produced by G
	- follow the direction of the arrows
	- compute the probability of a given sample from root to leaf
	- the $\hat\theta$ are the best parameters
		- best fit the data given the graph
- the second term is a penalty
	- to regularize
	- reduce number of parameters ($k$)
		- e.g in linear gaussian models the $k$ is the number of edges
			- for each edge we have a coefficient

Search Strategy
- how to avoid exaustive search
- is NP complete, we can constrain the search strategy
	- starting from a candidate graph
	- we select the one that maximize the score
- GES algorithm modify the DAG in a way to look into different MEC

GES algorithm
- three operations
	- insertion
	- deletion
	- reversal
- is able to retrieve the ground truth MEC from the ground truth DAG
- start from an empty graph (unconnected nodes)
- add a new edge and update
- if we don't improve the performance we stop adding
- same with deletion but with removing edge without worsening the situation
	- we shall remove edge because to maximize the score we want the least parameters as possible
		- remember the penalty term

For now, we got just to MEC. Not to ground thruth graph. 

### Additive Noise Model
![[Pasted image 20260303190306.png]]
We can have a reverse model with a possibly different gaussian noise term with the function g. That will fit the data as well as the true model
![[Pasted image 20260303190411.png]]

If the noise terms are not gaussian, Darmois-Strinovich theorem to distinguish between the two.

### Non linear Noise model

