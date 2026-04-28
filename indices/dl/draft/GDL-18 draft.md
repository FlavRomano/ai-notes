when rnn learns too much we need a mechanism to forget some knowledge

gating units
- local = effective on specific area of the input
- weighting to best expert through softmax gating

long short term memory
- internal state recurrence
- input gate decides 
	- how much of the input gets copied on g_t
- forget gate
	- how much of the forgot from the previous internal state
- output gate
- now very far away items in the sequence are closer in the memory

reservoir computing
- leveraging inductive bias to create reservoir 
- spectral ratio of jacobian matrix near 1
- stable network
- markovian property over echo-state property
