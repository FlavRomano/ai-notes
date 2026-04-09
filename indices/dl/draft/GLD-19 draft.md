size varying output, focus on some things (attention)

assembling the context is the tricky problem
- separation of concern and segregation between 
	- encoder
		- the one who create the context
		- compressed representation of the input sequence
	- decoder
		- the primer
		- decodes in an autoregressive manner

in the naive solution we risk to loose memory of the past (input $c$) the more we go deep
- everything is about on how I choose $c$ in the encode.

- teacher forcing
	- bias on "mistakes"
	- the best is to do a kind of simulated annealing
		- start teacher forcing
		- then stop it gradually

there is the one context
- each decoder output needs a custom context
	- soft-attention

soft-attention
- attention module
	- current hidden state of the rnn in output
		- context info $S$
	- hidden states in input
- custom context for generating the output in decoder
- powerful but high variance
	- maybe need a bit more of bias

weight sharing in the attention module
- possible but we lose the ordering matters
	- bad in NLP tasks
- convex combination
	- second layer is a softmax
	- sum up to 1

hard attention
- sampling with the most probable word each time in the attention module
- breaks differentiability
	- high variance
	- noisy gradient
		- we always need more sample
		- classical issue with sampling

local attention
- variation of the soft-attention with a little bit of bias
- add a neural network that decide 
	- which are the relevant input based on some inductive bias

attention is good because it has low inductive bias, but needs to learn all from data.