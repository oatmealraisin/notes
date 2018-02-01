# Week 9 - Ways to make neural networks generalize better

## Overview of ways to Improve Generalization

Overfitting happens because of sampling error. If the training data doesn't
perfectly model the distribution of the test data, there will be overfitting.

Ways to prevent overfitting
- Getting more data always helps
- Use a model with just enough capacity
  - Limit the number of layers and units per layer
  - Start with small weights and stop learning early (early stopping)
  - Penalize large weights (L1 & L2)
  - Add noise to the weights and activities
- Average many models
- Average many weight vectors (Bayesian)

Cross Validation
- Training data for learning parameters
- Validation data used to decide which metaparameters are best
- Test data to get a final estimate of how well the network works
- Do this N different times for N-fold xval

Early Stopping
- Best for when cross validation is too expensive
- As soon as validation performance gets worse, stop
- Weights do not have time to grow large
  - This causes hidden units to behave linearly
  - TODO: Watch "Why early stopping works" again, 9:30

## Limiting the Size of the Weights

Assumes a network with small weights is simpler than a network w/ large weights

We can add penalizers to the cost function
TODO: What is the difference between a cost function and a loss function

L2
- Penalize the squared weights
- Prevents the network from using weights it doesn't need
- Causes output to change more slowly over inputs

L1
- Penalize the abs value of the weights
- Drives weights to be 0 exactly

Weight constaints
- Better models the concept that weight ratios are important
TODO: Rewatch from last slide

## Using Noise as a Regularizer

How does noise become an L2 regularizer?
- Suppose Gaussian noise
- For input Noise
  - The variance of the noise is amplified by the squared weight
  - On input layers, x\_i input becomes x\_i + N(0, variance\_i)
  - On output layers, y\_j becomes y\_j + N(0, variance\_i \* w\_i^2)
    - This makes an interesting contribution to the error
- For weight noise
  - Trade a sigmoid activation function for a binary stochastic activation
function.
  - This means that the sigmoid activation function is instead finding
the _probability_ that the unit will be on.

## Introduction to the Full Bayesian Approach

TODO: Rewatch this

Instead of looking for a most likely parameter, we consider the all parameters,
and decide which is most probable given the data we observe

Recap of Bayes' Theorem:
- Bayes' theorem is stated mathematically as the following equation:
  - P(A|B) = P(B|A)\*P(A) / P(B)
- P(A|B) is a conditional probability: the likelihood of event A occurring given
that B is true. It is called the posterior.
- P(B|A) is also a conditional probability: the likelihood of event B occurring
given that A is true. It is called the likelihood.
- P(A) and P(B) are the probabilities of observing A and B independently of each
other; this is known as the marginal probability, or the prior and evidence,
respectively. The evidence acts to normalize the equation.

### Maximum likelihood

Bayesian Framework
- Assumes we have a prior distribution for everything
  - Start with uniform distribution over all posibilities
- Scale everything so that the posterior is normalized (area under = 1)

A new Bayes' Theorem:
- p(D)p(W|D) = p(D,W) = p(W)p(D|W)
  - Divided by p(D) gives normal Bayes' Theorem

These are covered in Chpt 2 of NN for Pattern Recognition

## The Bayesian Interpretation of Weight Decay

TODO: Rewatch this

### Maximum A Postoriori Learning (MAP)

TODO: What do the last 4 videos have to do with generalization?
output = y\_c = f(input\_c, W)
p(t\_c|y\_c) = e^-((t\_c - y\_c)^2/(2\*variance))/sqrt(2pi\*variance)

- Bayesian approach is to find the full posterior over all weights
- This is expensive

We are trying to minimize the negative log probabilities of the weights given
the data.

## MacKay's Quick and Dirty Method of Setting Weight Costs

Pronounced "Mack-Eye"

We can interpret weight penalities as doing MAP estimation so that the magnitude
of the weight penalty is related to the prior distribution over the weights

TODO: I still don't understand this

- **We don't need a validation set with this**

## References
