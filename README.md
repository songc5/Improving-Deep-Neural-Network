# Improving-Deep-Neural-Network
## Initialization:
A well chosen initialization can:
* Speed up the convergence of gradient descent
* Increase the odds of gradient descent converging to a lower training (and generalization) error

Three initialization methods compared in this project:
* Zeros initialization -- setting initialization = "zeros" in the input argument.
* Random initialization -- setting initialization = "random" in the input argument. This initializes the weights to large random values.
* He initialization -- setting initialization = "he" in the input argument. This initializes the weights to random values scaled according to a paper by He et al., 2015.
For the same number of iterations and same hyperparameters the comparison is:

| Model    			| Train accuracy |
| ------ | ----- |
| zeros initialization |  50%		|
| large random initialization | 83% |
| He initialization	| 99% |

## Regularization
Regularization can prevent overfitting
### l2 regularization
L2-regularization relies on the assumption that a model with small weights is simpler than a model with large weights. Thus, by penalizing the square values of the weights in the cost function you drive all the weights to smaller values. It becomes too costly for the cost to have large weights! This leads to a smoother model in which the output changes more slowly as the input changes.
* The value of λ  is a hyperparameter that you can tune using a dev set.
* L2 regularization makes your decision boundary smoother. If λ  is too large, it is also possible to "oversmooth", resulting in a model with high bias.

### dropout regularization

The idea behind drop-out is that at each iteration, you train a different model that uses only a subset of your neurons. With dropout, your neurons thus become less sensitive to the activation of one other specific neuron, because that other neuron might be shut down at any time.

| Model    			| Train accuracy | Test accuracy |
| ------ | ----- | --- |
| without regularization |  95%		| 91.5% | 
| l2 regularization | 94% | 93% |
| dropout regularization	| 93% | 95% |

Note that regularization hurts training set performance! This is because it limits the ability of the network to overfit to the training set. But since it ultimately gives better test accuracy, it is helping your system.

## Gradient checking
- Gradient checking verifies closeness between the gradients from backpropagation and the numerical approximation of the gradient (computed using forward propagation). 
- Gradient checking is slow, so we don't run it in every iteration of training. You would usually run it only to make sure your code is correct, then turn it off and use backprop for the actual learning process
