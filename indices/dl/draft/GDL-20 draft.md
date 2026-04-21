self attention
- linear
- the score is calculated by q query for each key of inputs
	- sum to one (convex  combination)
	- **the output is global**
- before in rgnn the input gets multiplied by the score after the softmax
	- now the original input is substituted by the "value"
- **can be done in parallel**
- it outputs the embedding ($c_q$ previously was the context) for the q-th input


separation of key and query
- more expressiveness because allows asymmetric relationships (queries)

very high variance
- flatten the score because low the softmax bell (saturation)
	- the solution is scaling the softmax by squared $d_k$

attention head
- one embedding for each of the input
- single queries, keys and values matrices 
- when we have multiple head
	- we got multiple single queris, keys and values matrices
		- head specific parameters
	- typically 4 attention head
		- we got multiresolution representation of the token
		- captures more things
			- semantically a word can have multiple role in a phrase
			- 4 different interpretations of the same word in different contexts
		- 4 embedding in output for each input word

positional encoding
- otherwise ordering is irrelevent in self attention 
	- lack of inductive bias
	- treat a phrase as "bag of words" rather than a phrase
	- we need to inject positioning
- $\tilde{x}_{n}$ gets semantic and position
- we need something linear though, because self attention is linear
	- so the encoding can't have distance in it
		- is non linear
	- sinusoidal encoding

sinusoidal encoding (absolute positional encoding)
- odd position sinusoid value
- even position cosinusoid value
- it's like a continuous version of bit encoding
	- equivalence of bit flipping
- the difference (distance) between two embeddings can be computed linearly
	- perfect for self attention

transformers
- no recurrence
	- no bias towards ordering
- encoder-decoder architecture
- causal attention problem
	- masking attention, in the decoder we don't want to look at future tokens
		- future tokens have low score
- $H$  contains the output embeddings
- residual connection that gets add with the mutli head attention output
	- smoothen learning
	- then normalization
		- we normalize the representation, not across the tokens (they are not iied)
- MLP gives non-linearity

parameter sharing = parallelism

we solve gradient propagation in the attention layer
- on the first layer (the attention layer) we have 1 step of propagation of the gradient
- is matching everything with everything
- but the operation is not cheap $O(n^2)$