# Week 6 - Optimization: How to Make the Learning Go Faster

## Overview of mini-batch gradient descent

### What is the error surface for a neuron?

- A surface where the horizontal axes are the weights of a neuron, and the
vertical axis corresponds to the error of the neuron.
- Going downhill reduces error, but does not point at the minimum
  - This causes oscillations

### Stochastic Gradient Descent

- If the dataset is highly redundant, running over the whole dataset is almost
useless.
- Mini-batch solves this problem, because it breaks the training data into many
rounds of gradient descent.
  - This assumes proper distribution of training classes over the batches
  - Mini-batch also includes tuning the learning rate towards healthy gradient
  descent

## A bag of tricks for mini-batch gradient descent

- Smart initialization
  - If two units have the same parameters, they will remain the same.
  - Initializing the weights to small random values.
- Shifting the inputs
  - Moving the inputs towards having a mean of 0 creates a less elongated error
  surface
- Scaling the inputs
  - Change the inputs to be of the same distribution between [-1, 1]
- Decorrelate the inputs
  - PCA, drop the smallest eigenvalues

## The momentum method

- SGD + mini-batch + momentum is most common method
- Based on the idea of loss optimization as gravity
- Creates a residual effect of consistent direction
  - This allows us much larger learning rates
- v(t) = \alpha * v(t - 1) - \epsilon * (dE/dw)
- \delta w(t) = v(t)
- Start with a small momentum

v(infinity) = 1/(1-\alpha) * (-\epsilon * (dE/dw))

### Nesterov Method

- Normal momentum calculates gradient at w(t) location, then uses that gradient
to do momentum movement
- Instead, calculate gradient at w(t+1) location, then use that gradient to do
momentum movement
  - Better to gamble, then correct, rather than correct, then gamble
  - 7:30 has very good graphic for this

## Adaptive learning rates for each connection

- Each connection in the NN should have its own learning rate
  - NOT the same as momentum, can be combined
  - Designed for full-batch learning
  - Only deals with axis-aligned effects
- Gradients at deep layers can get very very small
- Take global learning rate, multiply by local gain
  - Gain starts at 1
  - \delta w\_ij = -\epsilon g\_ij * (dE/dw\_ij)
  - (dE/dw\_ij)(t)\*(de/dw_ij)(t-1) > 0: g\_ij(t) = g\_ij(t-1) + 0.5
  - (dE/dw\_ij)(t)\*(de/dw_ij)(t-1) < 0: g\_ij(t) = g\_ij(t-1) \* 0.95
- Important to limit gains
  - [0.1, 10], [0.01, 100]


## RMSPROP: Divide the gradient by a running average of its recent magnitude

# TODO: Watch this again

- Combines the ALR idea of using gradient signs with adapting step size
  - Both increases and Decreases are multiplicative
  - Can be combined with Nesterov momentum

## References

[Nesterov 1983]()
[Sutskever 2012]()
[Jacobs, 1989]()
[Yann Lecun "No more pesky learning rates"]()
