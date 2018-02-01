Learning layers of features by stacking RBMs
--------------------------------------------

What is a DBN?
- A deep network which is a combination of RBMs and Belief nets
- Uses stacked RBMs to learn features
- Each RBM models the patterns of activity of the previous.
- v <- h(belief net) <- h(RBM) <-> h(RBM) (for example)
- uses wake/sleep algorithm for training belief net, using W' for wake weights
  and W for sleep weights

What is a factorial distribution?
- A distribution where the probability of two events occuring is the product of
  each event occuring individually.
- Average of a factorial distribution is not factorial
- In an RBM, the posterior over hidden units is factorial for each visible vector

Important distributions: p(v|h), p(h|v), p(v,h), p(h), p(v)

TODO: Need more notes after 10min

Discriminative learning for DBNs
--------------------------------

What is pre-training?
- What we described in the previous lecture (contrastive wake-sleep)
- Backpropagation finishes the job.

Why pre-train?
- Scales well if we have large networks with locality
- Less overfitting, because most information comes from distribution modeling,
  as opposed to label modeling. This allows us to create actual feature
  detectors.
- Disadvantage: we may learn useless features

What is locality?
- Features are grouped by location
- Convolutional layers are an example

What happens during discriminative fine-tuning?
-----------------------------------------------



Modeling real valued data with an RBM
-------------------------------------

How do I use an RBM to model real-valued data
- Visible units are linear units w/ Gaussian noise
- Hidden units are ReLU units

In real pictures, the intensity of a pixel is almost always the same as the
average of it's neighbors

RBMs are infinite sigmoid belief nets
-------------------------------------

References
----------

[Platt, Hinton]()
[Decoste & Shoelkopf, 2002]()
[Hinton & Salakhutdinov, 2006]()
[Ranzato et al., NIPS 2006]()
[Mohamed, Dahl, Hinton, 2009 & 2012]()
[Erhan et al, AISTATS 2009]()
Yoshua Benjio
