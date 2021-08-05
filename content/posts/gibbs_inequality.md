+++
title = "Gibbs' Inequality"
author = ["Jethro Kuan"]
draft = false
+++

The relative entropy or [kl divergence]({{<relref "kl_divergence.md#" >}}) between two probability
distributions \\(P(x)\\) and \\(Q(x)\\) defined over the same alphabet
\\(\mathcal{A}\_X\\) is:

\begin{equation}
  D\_{\textrm{KL}}(P||Q) = \sum\_{x} P(x) \log \frac{P(x)}{Q(x)}
\end{equation}

Gibbs Inequality states that:

\begin{equation}
  D\_{\textrm{KL}}(P||Q) \ge 0
\end{equation}

for any \\(P\\) and \\(Q\\).