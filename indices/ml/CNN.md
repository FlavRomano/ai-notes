1.  **Motivation for CNNs**
    *   Limitations of standard fully connected networks for images.
	    * too many parameters
	    * lack of invariance
    *   Exploiting architecture design for prior information: Local connections and Weight-sharing.

2.  **Core Components: Convolution**
    *   The mathematical concept of Convolution (sliding weighted average).
    *   1D Convolution (Time-Delay NN) and 2D Convolution details.
    *   Key parameters: Kernels/Filters, Local Receptive Fields, Padding, and Stride.
    *   Feature maps and translation invariance.

3.  **Core Components: Pooling**
    *   Subsampling methods: Max Pooling and Mean Pooling.
    *   Role of pooling: Dimensionality reduction and invariance to small distortions.

4.  **CNN Architecture**
    *   Structure: Stacking Convolutional, Pooling, and Fully Connected layers.
    *   Hierarchical feature abstraction (low-level to high-level features).
    *   Summary of advantages: Parameter reduction (regularization) and spatial processing.

5.  **History and Evolution**
    *   **LeNet:** Architectures and performance on MNIST.
    *   **Deep MLP:** comparison using GPU acceleration.
    *   **AlexNet & ImageNet:** The 2012 breakthrough, ReLU, and Dropout regularization.
