# Week 3

## Learning the weights of a linear neuron

TODO:

## The error surface for a linear neuron

TODO:

## Learning the weights of a logistic output neuron

TODO:

## The backpropagation algorithm

* Single layer networks are not very powerful (XOR)
* Adding a layer of hand-coded features is hard

We could randomly change weights slightly
* Nah

* We don't know how hidden weights should change
* We take the error backwards over the connections between neurons

Using MSE:
dE / dy_j = -(t_j - y_j)
* This is only for the output neuron, and starts EBP

We want to know dE/dz_j

We want to find dE/dw_ij

dE/dz_j = (dy\_j / dz\_j) \* (dE/dy\_j) = y\_j(1-y\_j) \* dE/dy\_j =
-y\_j(1-y\_j)(t-y\_j)

dE/dy_i = sum_j(dz_j/dy_i \* dE/dz_j) = sum_j(w_ij * dE/dz_j)

dE/dw_ij = dz_j/dw_ij * dE/dz_j = y_i dE/dz_j

## Using the derivatives computed by backpropagation

TODO:

## References
