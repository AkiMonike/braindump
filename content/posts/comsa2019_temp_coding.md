+++
title = "Temp Coding with Alpha Synaptic Function"
author = ["Jethro Kuan"]
draft = false
+++

tags
: [Spiking Neural Networks]({{<relref "spiking_neurons_lit_review.md#" >}})


## Temporal Coding with Alpha Synaptic Function ([Comsa et al., n.d.](#org629ba50)) {#temporal-coding-with-alpha-synaptic-function--comsa-et-al-dot-n-dot-d-dot--org629ba50}


### Motivation {#motivation}

1.  Atemporal networks (think LSTMs) don't have the benefits of
    encoding information directly in the temporal domain
    1.  They remain sequential (require all previous layers of
        computation to produce answer)
    2.  Information in the real world are typically temporal


### Key Ideas {#key-ideas}

1.  **Temporal Coding**: Information is encoded in the relative timing of
    neuron spikes. Using temporal coding allows shift of differentiable
    relationship into the temporal domain.
    1.  Find differentiable relationship of the time of postsynaptic
        spike with respect to the weights and times of the presynaptic
        spikes.

2.  **Alpha synaptic transfer function**: Use the SRM, but with the
    exponential decay of form \\(t e^{-t}\\).

3.  **Synchronization pulses:** input-independent spikes, used to
    facilitate transformations of the class boundaries.


### The Coding Scheme {#the-coding-scheme}

More salient information about a feature is encode as an earlier
spike in the corresponding input neuron (think time-to-first-spike).

In a classification problem with \\(m\\) inputs and \\(n\\) possible classes:

input
: spike times of \\(m\\) input neurons

output
: index of output neuron that fires first (among the \\(n\\)
    output neurons)


### Alpha Synaptic Function {#alpha-synaptic-function}

Incoming exponential synaptic kernels are of the form \\(\epsilon(t) =
\tau^{-1}e^{-\tau t}\\) for some decay constant \\(\tau\\). Potential of
membrane in response to the spike is then \\(u(t) = t e^{-\tau t}\\). It
has a gradual rise, and slow decay.

{{< figure src="/ox-hugo/screenshot_2019-08-30_13-21-44.png" caption="Figure 1: Plot of \\(y = x e^{-10x}, x \in [0, 1]\\)" >}}


### Modelling Membrane Potential {#modelling-membrane-potential}

The membrane potential is a weighted sum of the presynaptic inputs:

\begin{equation}
  V\_{mem}(t) = \sum\_{i} w\_i (t-t\_i)e^{\tau(t\_i - t)}
\end{equation}

We can compute the spike time \\(t\_{out}\\) of a neuron by considering the
minimal subset of presynaptic inputs \\(I\_{t\_{out}}\\) with \\(t\_i \le
t\_{out}\\) such that:

\begin{equation} \label{eqn:threshold}
  \sum\_{i \in {I\_{t\_{out}}}} w\_i \left( t\_{out} - t\_{i} \right)
  e^{\tau (t\_i - t\_{out})} = \theta
\end{equation}

<a name="eqn:threshold"></a> has 2 solutions: 1 on rising part of function and
another on decaying part. The spike time is the earlier solution.


### Solving for the Equation <a name="eqn:threshold"></a> {#solving-for-the-equation}

Let \\(A\_{I} = \sum\_{i \in I} w\_i e^{\tau t\_i}\\), and \\(B\_{I} = \sum\_{i
\in I} w\_i e^{\tau t\_i} t\_i\\), we can compute:

\begin{equation}
  t\_{out} = \frac{B\_I}{A\_I} - \frac{1}{\tau}W\left( -\tau
  \frac{\theta}{A\_I}e^{\tau \frac{B\_I}{A\_I}} \right)
\end{equation}

where \\(W\\) is the [Lambert W function](https://en.wikipedia.org/wiki/Lambert%5FW%5Ffunction).


### The Loss Function {#the-loss-function}

The loss minimizes the spike time of the target neuron, and maximizes
the spike time of non-target neurons (cross-entropy!)

Softmax on the negative values of the spike times \\(o\_{i}\\) (which
are always positive):

\begin{equation}
  p\_j = \frac{e^{- o\_j}}{\sum\_{i=1}^{n} e^{- o\_i}}
\end{equation}

The cross entropy loss \\(L(y\_i, p\_i) = - \sum\_{i=1}^{n} y\_i \ln p\_i\\) is
used.

Changing the weights of the network alters the spike times. We can
compute the exact derivative of the post synaptic spike time wrt any
presynaptic spike time \\(t\_j\\) and its weight \\(w\_j\\) as:

\begin{equation}
  \frac{\partial t\_{out}}{\partial t\_j} = \frac{w\_j e^{t\_j} \left( t\_j
      - \frac{B\_I}{A\_I} + W\_I + 1\right)}{A\_I (1 + W\_I)}
\end{equation}

\begin{equation}
  \frac{\partial t\_{out}}{\partial w\_j} = \frac{e^{t\_j} \left( t\_j
      - \frac{B\_I}{A\_I} + W\_I + 1\right)}{A\_I (1 + W\_I)}
\end{equation}

where

\begin{equation}
  W\_I = W\left( -\frac{\theta}{A\_I}e^{\frac{B\_I}{A\_I}} \right)
\end{equation}


### Synchronization Pulses {#synchronization-pulses}

These act as a temporal form of bias, adjusting class boundaries in
the temporal domain. Per network, or per layer biases are added. Spike
times for each pulse are learned with the rest of the parameters of
the network.


### Hyperparameters {#hyperparameters}

{{< figure src="/ox-hugo/screenshot_2019-08-30_13-52-12.png" >}}


## Experiments {#experiments}


### Boolean Logic Problems {#boolean-logic-problems}

Inputs encoded as individual spike times of two input neurons. All
spikes occur between 0 and 1. True and False values are drawn from
distributions \\([0.0, 0.45]\\) and \\([0.55, 1.0]\\) respectively.

Trained for maximum of 100 epochs, 1000 training examples. Tested on
150 randomly generated test examples. 100% accuracy on all problems.


### Non-convolutional MNIST {#non-convolutional-mnist}

784 neurons of the input layer corresponding to pixels of the image.
Darker pixels encoded as earlier spike times. Output of network is the
index of the earliest neuron to spike.

Trained with evolutionary-neural hybrid agents. Best networks achieved
99.96% and 97.96% accuracy on train and test sets.

The network learns two operating modes: slow-regime and fast-regime.
Operating in the slow regime has higher accuracy, but takes more time.
Fast regime makes quick decisions, with the first spike in the output
layer occurring before the mean spike in the hidden layer.

{{< figure src="/ox-hugo/screenshot_2019-08-30_14-05-59.png" >}}


## Bibliography {#bibliography}

<a id="org629ba50"></a>Comsa, Iulia M., Krzysztof Potempa, Luca Versari, Thomas Fischbacher, Andrea Gesmundo, and Jyrki Alakuijala. n.d. “Temporal Coding in Spiking Neural Networks with Alpha Synaptic Function.” <http://arxiv.org/abs/1907.13223v1>.