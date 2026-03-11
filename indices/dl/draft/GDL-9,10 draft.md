intro to hmm
- we work on sequences
	- collection of observations over time
		- $y^1, \dots, y^N$ 
		- the single sequence in the dataset is i.i.d
			- but the whole dataset is not
		- the length could differ (different sequence => different length)
			- bayesian network length change from sequence to sequence
			- we solve it with weight sharing (stationarity)
	- dependent observations
	- complete ordering of observation regulated by time\

First-order Markov chain
- simplest model that accounts intra dependencies between sequences
- first-order assumption based on Markov casual chain structure
	- $t-1$ to $t$, forget everything else
	- all observable data (shaded)
- we can simplify the joint distribution
	- choose ordering
		- in this case that follows time
	- apply chain rule
	- a lot of path are blocked, so we can simplify a lot of conditional probabilities
		- we left with $$P(Y_{1},\dots,Y_{T}) = \underbrace {P(Y_{1})}_{\text{prior}} \prod_{t=2}^T P(Y_{t} \mid Y_{T-1})$$
			- we implicitly applying stationarity
			- the prod will have the same parameters without considering the time
		- the prior in the example is a multinomial
			- we can learn it by maximum likelihood
				- counting how many times appears a letter then divide by 25
			- vector of probabilities $$\Pi$$
		- probability of seeing a "c" followed by an "a"
			- stationarity tell us that this probability never change over the sequence $$A$$
			- we are reusing the same set of parameters
		- the other probability distribution is a bunch of multinomial
			- a matrix of probabilities
				- observing a letter $y$ after another one $y'$
				- transitioning from one symble to another one
- to compute probability of observing $P(Y_{t} = y)$ we marginalize $$\sum_{y'\in \{ a\dots z \}} P(Y_{t} = Y, Y_{t-1} = Y') = \underbrace{\sum_{y'} P(Y_{t} = Y \mid Y_{t-1}= Y') }_{A} P(Y_{t-1} = Y')$$
	- we apply the same concept with $P(Y_{t-1})$ and so on until I get $P(Y_{1})$
	- $A$ is a matrix so we can rewrite it as $$P(Y_{t} = Y) = A^{t-1} \Pi$$
		- we are just iterating the power of the transition matrix row

First order Markov chain
- bayesian network that respect the first order markov assumption

Hidden Markov Model
- markov chain between unobservable state
	- each state generate an evidence (observable)
- introducing hidden states in $P(\overline Y)$ by marginalization over all possible states values
- emission distribution
	- emits $Y_1$ at time $1$ ... $$b_{1}(Y_{1})$$
	- modelled by $c$ gaussians
		- temporal clustering (important)
- the charaterizing distribution for hmm are the same of markov model  with emissions $$\sum_{\overline S} P(S_{1}) P(Y_{1} \mid S_{1}) \prod_{t=2}^T P(Y_{t} \mid S_{t}) P(S_{t} \mid S_{t-1})$$

$$\Pi$$ is a vector $$\mathbb{R}^c$$ and $$A$$ is a matrix $$\mathbb{R}^{c \times c}$$

- smoothing
	- learn a hidden markov model with Expectation Maximization
		- so we estimate the posterior

- Forward backward algorithm
	- separating past from future
	- def cond ind.
	- introduce hidden state by marginalization
	- recursion
	- message passing from $t=1$ to $t=2$
		- $\alpha$ is a vector $$\mathbb{R}^{c}$$

---
GDL 10

- beta term $$\beta _{t+1}(i) = P(\overline y_{t+1:T} \mid S_{t} = i)$$
	- the conditioning on $S_t$ reminds of the conditioning $$P(S_{t+1}, S_{t})$$ so we'll see this distribution at some point
		- we will introduce the term by marginalization $$\sum_{j} P(\overline y_{t+1:T}, S_{t+1}= j\mid S_{t}= i)$$ the left term is the exactly the emission
		- by applying the def cond indipendence, we want to condition on $y_{t+1}$ $$\sum_{j} P(y_{t+1} \mid \overline y_{t+2:T}, S
		  _{t+1} = j , S_{t} = i) P(\overline y_{t+2:T}, S_{t+1} = j \mid S_{t} = i)$$
			- all future path are blocked by $S_{t}$ so everything else that comes next became pointless $$\sum_{j}  P(y_{t+1}\mid S_{t+1} = j)P(\overline y_{t+2:T}, S_{t+1} = j \mid S_{t} = i)$$
		- by applying again the def cond indipendence on $$P(\overline y_{t+2:T}, S_{t+1} = j \mid S_{t} = i)$$ moving the $S_{t+1} = j$ on the conditioning side we get something probability distribution multiplyed by the transition system $A$
			- again, we can get rid of $S_{t} = i$ on the probability distribution because the path is blocked
			- we obtained $\beta_{t+2}(j)$