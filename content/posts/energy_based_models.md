+++
title = "Energy-based Models"
author = ["Jethro Kuan"]
slug = "energy_based_models"
draft = false
+++

The energy surface is a "contrast function" that takes low values on the data manifold and higher values everywhere else. The key idea is to have low energy for the observed data, and high energy everywhere else.

It is easy to make energy low on seen samples, but more difficult to make energy high on unseen samples.

We can also reinterpret Principle Component Analyses and [K-means]({{<relref "k_means.md#" >}}) as energy-based models.


## Strategies to Shape the Energy Function {#strategies-to-shape-the-energy-function}

1.  Build the machine so that the volume of low energy stuff is constant:
    -   PCA, K-means, GMM, square ICA
2.  Push down the energy of data points, push up everywhere else
    -   Maximum likelihood (requires tractable partition function, or variational approximation)
3.  Push down the energy of data points, push up chosen locations
    -   Contrastive divergence, Ratio Matching,  Noise Contrastive Estimation, Min Probability Flow, Adversarial Generator/GANs
4.  Minimize the gradient and maximum curvature around data points
    -   Score matching
5.  If \\(F(Y) = ||Y - G(Y)||^{2}\\), then make G(Y) as constant as possible
    -   Contracting auto-encoder, saturating auto-encoder
6.  Train a dynamical system so that the dynamics goes to the data manifold
    -   Denoising auto-encoder, masked auto-encoder
7.  Use a regularizer that limits the volume of space that has low energy
    -   Sparse coding, Sparse auto-encoder, LISTA & PSD, Variational auto-encoder