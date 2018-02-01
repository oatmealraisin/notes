Week 15
=======

From PCA to autoencoders
------------------------

What is PCA?
- An algorithm that takes n-dimensional data and finds the M orthogonal
  directions in which the data has the most variance
- High dimensional data can be represented by lower-dimensional code

How can we use EBP to model this algorithm?
- Use the input as the target vector, with an N-dimensional input vector and an
  M-dimensional code vector in a hidden layer, output a recontructed
  N-dimensional vector.
- Projects higher dimensional data onto a lower dimensional plane.

Why would we use EBP?
- EBP is typically much less effficient
- Allows us to generalize PCA
- Non-linear layers allows us to project data onto a curved plane

Deep auto encoders
------------------

Became viable once pre-training was discovered, and computer became faster.
Hinton & Salakhutdinov
- 784 pixels -> 1000 -> 500 -> 250 -> 30 output
- Used stack of RBMs to initialize the encoding
- Decoding weights were W'
- Then used EBP to reconstruct images

Deep auto encoders for document retrieval
-----------------------------------------

Can use autoencoder with a bottleneck of 2 to represent things on a graph

How do we use autoencoders for document retrieval
- Old way was Latent Semantic Analysis. New way uses autoencoders
- Convert documents into bag of words
- 2000 element BOW -> 500 -> 250 -> 10
- Normalize the content of the BOW (1/N) for output comparison, due to the
  output softmax
- When training the first hidden RBM, multiply the weights by N, to represent
  actual sample amount
  - TODO: What happens when we do not do this?

Semantic Hashing
----------------

TODO: Go through this video again

What is semantic hashing?
- Converts documents into memory addresses, with similar documents in nearby
  addresses
- Gets multiple binary descriptors that are (hopefully) orthogonal
- 2000 element BOW -> 500 -> 250 -> 30
- Standard RBM pretraining with EBP

What is supermarket search?
- Flipping binary values in a SH address leads to similar documents that are
  similar along different features (size of bottleneck)

Learning binary coders for image retrieval
------------------------------------------

TODO: Go through this video again

Semantic hashing can allow us to search along similar images.
1024x3 (RBG) -> 8192 -> 4096 -> 2048 -> 1024 - 512 -> 256 output code
  - The architecture for this is a guess, there is no theory behind it

Shallow autoencoders for pre-training
-------------------------------------

What is a shallow autoencoder?
- A one-layer RBM is an example
  - Has very strong regularization
  - Does not work w/ Maximum Likelihood

Denoising autoencoders
- Adds noise by setting many input components to 0
- Acts like dropout

Contractive autoencoders
- Hidden activities are insensitive to the input
- Tend to have the property that only a small set of the hidden units are in the
  sensitive to the input

Hintons current view:
- When dataset doesn't have a lot of labels, pretraining is super useful


References
----------

TODO: Find references

[Hinton & Salakhutdinow, Science 2008]()
