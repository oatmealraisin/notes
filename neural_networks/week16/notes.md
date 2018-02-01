Week 16
=======

Learning a join model of images and captions
--------------------------------------------

Previous methods don't use captions for learning, which could be useful

Modeling the joint density of images and captions
- Train a multilayer model of images using a Deep Bolzmann Machine
- Train a separate multilayer model of word-count vectors
- Feed those into a new top layer, use joint training to improve
  - Using a DBM allows the two models to change eachother in joint training

Hierarchical Coordinate Frames
------------------------------

Bayesian Optimization of Hyper Parameters
-----------------------------------------

References
----------

TODO: Find references

[Srivastava & Salakhutdinov, NIPS 2012]()
