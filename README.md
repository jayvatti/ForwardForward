# ForwardForward Implementation

The `forwardForward.ipynb` notebook contains the implementation of the ForwardForward algorithm, inspired by the human brain's information processing mechanisms. The model utilizes ReLU activations and is trained on 50,000 images, with evaluation performed on 10,000 test images. Labels are augmented by adding them to the first 10 pixels of each image.

## Notebooks

- [ForwardForward Implementation](forwardForward.ipynb)
- [ForwardForward with Residual Adjustments](forwardForward_adjustments.ipynb)
- [Multi-Layer Perceptron (MLP) Comparison](mlp.ipynb)
- [Playground](tests.ipynb)

## Implementation Details

- **Activation Function:** ReLU
- **Training Data:** 50,000 images
- **Testing Data:** 10,000 images
- **Label Augmentation:** Labels added to the first 10 pixels
- **Threshold:** 2.0
- **Epochs:** 50
- **Peer Norm Coefficient:** 0.1
- **Optimizer:** Adam with learning rate 0.03
- **Negative Data:** Incorrect labels used as negative data
- **Training Procedure:** After the first pass of training all layers, negative data is iteratively reduced by eliminating incorrect examples up to 10 times, maintaining both positive and negative data.

## Adjustments: Residual Connections

To enhance the ForwardForward model's performance, residual connections were incorporated. Residual connections allow the network to map input features directly to outputs via a scaled projection, mimicking the brain's ability to integrate raw sensory input with processed information. This adjustment ensures efficient and robust learning by preserving critical information throughout the layers.

### Key Adjustments

- **Residual Scale:** Set to 0.4 to control the contribution of the residual projection.
- **Residual Projection Layer:** Implemented using a linear layer without bias to project input dimensions to output dimensions.
- **Peer Norm Coefficient:** Adjusted to 0.01 to stabilize training.

These adjustments facilitate the flow of information through the network, preventing the loss of crucial features and improving generalization.

## Results

| Model                         | Train Accuracy | Train Error | Test Accuracy | Test Error |
|-------------------------------|-----------------|-------------|----------------|------------|
| ForwardForward (before adj)   | 95.92%          | 4.08%       | 95.75%         | 4.25%      |
| ForwardForward (after adj)    | 98.16%          | 1.84%       | 96.68%         | 3.32%      |
| MLP                           | -               | -           | 97.78%         | 3.02%      |

**Summary of Results:**

- **ForwardForward (before adjustments):**
  - **Train Accuracy:** 95.92%
  - **Train Error:** 4.08%
  - **Test Accuracy:** 95.75%
  - **Test Error:** 4.25%

- **ForwardForward (after adjustments):**
  - **Train Accuracy:** 98.16%
  - **Train Error:** 1.84%
  - **Test Accuracy:** 96.68%
  - **Test Error:** 3.32%

- **Multi-Layer Perceptron (MLP):**
  - **Final Test Accuracy:** 97.78%

The introduction of residual connections significantly improved the ForwardForward model's performance, achieving higher training and testing accuracies while reducing error rates. The MLP model also demonstrates competitive test accuracy, validating the effectiveness of the ForwardForward approach with residual enhancements.

## Potential Improvements in the Adjustment 
A potential improvement explored was the implementation of residual connections within the ForwardForward model. Residual connections allow the network to map input features directly to outputs via a scaled projection, meaning that the input features' scaling is adjusted before passing through the output. This enables input data to bypass certain layers and transformations, preventing the loss of crucial information and enhancing the model's generalization capabilities.

By integrating residual connections, the model benefits from improved information flow, reduced risk of vanishing gradients, and better preservation of essential features. This adjustment not only aligns the model more closely with the brain's information processing strategies but also contributes to more robust and efficient learning.

## Future Improvements

For future enhancements, I plan to experiment with integrating additional biologically inspired mechanisms to further align the ForwardForward model with human brain functionalities. Some of the features I aim to explore include:

### 1. **Predictive Coding**
- Implement a mechanism where the model anticipates incoming data and minimizes prediction errors, enhancing its ability to learn from discrepancies between expected and actual inputs.

### 2. **Hebbian Learning**
- Incorporate a learning rule where connections strengthen based on the co-activation of neurons, promoting more efficient and meaningful feature representations.

### 3. **Homeostatic Plasticity**
- Introduce mechanisms to maintain balanced activity levels within the network, ensuring stability and preventing issues like neuron saturation.

### 4. **Sparse Coding**
- Encourage sparsity in activations to achieve more efficient and interpretable representations, mirroring the brain's tendency for sparse neural firing.

### 5. **Neuromodulation**
- Add neuromodulatory elements, such as reward-based learning signals, to dynamically adjust learning rates and enhance adaptive learning behaviors.

Integrating these features could further improve the model's robustness, generalization, and alignment with cognitive processes observed in the human brain.
