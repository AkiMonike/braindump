+++
title = "Multi-modal Fusion"
author = ["Jethro Kuan"]
slug = "multimodal_fusion"
draft = false
+++

Multi-modal fusion is the integration of information from multiple
modalities with the goal of predicting an outcome measure (e.g.
classification, or regression).

Multi-modal fusion is motivated by 3 main reasons:

1.  Access to multiple modalities help make predictions more robust
    (e.g. in AVSR)
2.  Multiple modalities may capture complementary information
3.  Multi-modal systems can still operate when some modalities are
    missing

Multi-modal fusion approaches can be classified as
([Baltrušaitis, Ahuja, and Morency, n.d.](#org08a5e8e)):

- **Model-agnostic**
  - early fusion
  - hybrid fusion
  - late fusion
- **Model-based**
  - kernel-based
  - graphical models
  - neural networks

## Model-agnostic Approaches {#model-agnostic-approaches}

Early fusion approaches integrate features immediately after they are
extracted (for example, via concatenation). Late fusion performs
integration after each of the modalities make a decision, for example
via averaging. Hybrid fusion combines outputs form early fusion, and
individual unimodal predictors.

Model-agnostic approaches are easy to implement using uni-modal
machine learning methods.

## Model-based Approaches {#model-based-approaches}

These approaches are tailored towards handling multi-modal data.

[Multiple Learning Kernel]({{<relref "multiple_learning_kernel.md" >}}) (MKL) methods extend kernel [Support Vector
Machines]({{<relref "support_vector_machines.md" >}}) to use different kernels for different modalities.
Modality-specific kernels allow for better fusion of heterogeneous
data. One advantage of MKL is that the loss function is convex, which
leads to easy optimization and globally optimum solutions. However,
MKL approaches rely on support vectors (training data) at test time,
which means inference can be slow.

Generative graphical models such as factorial hidden markov networks, or
multi-stream hidden markov metods have been used. Discriminative
models such as [Conditional Random Fields]({{<relref "conditional_random_fields.md" >}}) sacrifice the modeling of
joint probability for predictive power.

Lastly, neural networks fuse temporal multimodal information through
RNNs and LSTMs. These approaches have also been adapted for various
image captioning tasks. Neural networks have the capacity to learn
from large amounts of data, and are able to learn complex decision
boundaries. However, they lack interpretability, and require large
amounts of training data.

## Bibliography {#bibliography}

<a id="org08a5e8e"></a>Baltrušaitis, Tadas, Chaitanya Ahuja, and Louis-Philippe Morency. n.d. “Multimodal Machine Learning: A Survey and Taxonomy.” <http://arxiv.org/abs/1705.09406v2>.
