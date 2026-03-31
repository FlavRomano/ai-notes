sequential data
- not iied
	- e.g considering complete ordering
- assuming for timeseries the past as context 
	- a point at time $t$ can be described by its context

recurrent layer
- compress the context of inputs
	- state $h_t$
	- interpret the input based on the internal state
		- it's like the context for a word
- returns a vector of neural activation

vanilla rnn
- two sets of weights
	- W_in
	- W_h
- input at time $t$
- state at time $t$ requires state at time $t-1$
- unfolding
	- as hmm
	- same layers but copied
		- weight sharing
		- local potential

unfolding rnn
- fixed set of weights fixed reused over time
- unfolding the model on the data
	- copy a layer as many times as $t$
		- now it becomes a deep neural network
		- each layer has the same weight 
- stationarity w.r.t time
	- as hmm

vanishing gradient
- spectral property of D and W_h

forward passing may be leaking
- analyze with sensitivity analysis
	- check the norm
	- Jacobian appears
- our ability of retain information in memory is influenced by
	- choice activation function
	- choice weight matrix
- physical dynamical system told us how to conserve some property (the memory) by observing something in the Jacobian.
- generalize poorly, two things similiar but slighly perturbeted gets projected far apart on the memory encoding
	- should be similiar but gets classified differently
		- same history => same prediction