- semantic segmentation
	- image part classification

- cnn
	- is applied to sequences
	- weight sharing
		- 15 subwindow input
		- 16 weights 
		- multiplication then shift (sliding window)
			- convolution operation
	- we don't use MLP (doesn't have any type of invariance)
		- because weight are location based
			- can't generalize a shifted image for example
			- weights are bounded to the position of the pixels
		- we introduce symmetries properties

- convolution
	- equivalent of simple cells
	- smoothing operator (averaging operator)
		- weighting-average between image and kernel over time
			- kernel can be interpret as the neuron
	- 2d convolution
		- 25 multiplications with weights (contained in the filter) and input (the portion of image) + bias
	- 3d convolution
		- a single kernel channel is applied to a single image channel
			- at the end of the summation we get a single image with a single channel
				- the output image have the same size of the number of convolution operation did
					- we can do downsampling and reducing computational cost by doing striding > 1
			- we get a matrix of interpretation of what the kernel saw in the image, not just a new image
				- a feature map
	- it's a linear operator
		- so it's not very good
		- we need non-linearity
			- LeNet uses sigmoids as activation function
			- better ReLU
	- we apply the activation function to the feature matrix
	- is positional invariant BUT not rotational invariant

- pooling
	- aggregation operation
		- after convolution
		- we lose resolution (on purpose)
	- gives rotational invariant (is also transational invariant)
	- equivalent of complex cells
	- operates after the feature map
		- not every one...
	- filters are even and stride to not overlap
	- abstraction mechanism
		- we can decouple higher abstract concept from the actual image itself

- convolutional layer
	- filter then nonlinearity then pooling
	- then output is inputed to the next convolutional layer

- the more the image shrink because of the pooling
	- the kernel gets bigger
		- because the feature learned to recognize at the end of the pipeline are more complex
		- we compress the semantic meaning
	- at the last convolutional layer we want the feature map smaller as possible
		- because then it will be the input of Fully connected layer
		- which is the suffering part
			- the training in MLP

- filter banks
	- number of parameters $K \times K \times D_{I} \times D_{K}$
		- we drop the channel at kernel level
		- but because we got $K$ kernels we got as a feature map a $H' \times W' \times D_{K}$, where the number of kernels became the number of channels
			- we didn't lose channel at all, ready for pooling $H'' \times W'' \times D_{K}$

- sparsity
	- not every input is connected to every output
		- the other connection are weighted 0
		- reduce parameters
	- introducing striding the sparsity increase
		- makes the convolutional layer sparser

- design choice on pooling
	- max pooling
		- translational invariance
		- not rotational invariance
	
	- cross channel pooling
		- rotational invariance
		- size invariance
		- color invariance
		- etc...

- single neuron
	- the deeper is the broader input samples looks
	- higher abstraction

---

training cnn

- deconvolution
	- is equals to upsampling
	- this technique can be used to throw away the noise
		- convolution, compression then deconvolution
		- throw redundant informations or useless informations

- googlenet
	- not using dense layers
	- use intermediate result (output layers) as checkpoint
		- if the gradient dies we can restart from another checkpoint
	- 1x1 convolution
		- to compress stuff
	- obtain rich representation at multiple level

- batch normalization
	- way to control variance
	- layer with gamma and beta parameters
		- learnable
	- standard de facto in mini batch with deep architecture and independent data (i.i.e)
		- if data are dependent this thing doesn't work
			- like sequence

- resnet
	- large scale tasks
	- propagation effect
		- on gradient descent error correction the copied part has gradient 1
			- the signal flows propagating the adjusted error
		- we batch normalize after every residual
			- to avoid variance amplification (we accumulate variance)

- dense cnn
	- good for small tasks
	- all layers see all features of the previous layers
		- we get a similiar effect of resnet
			- powerful representation
			- more multiplication and more complex in terms of memory

- 