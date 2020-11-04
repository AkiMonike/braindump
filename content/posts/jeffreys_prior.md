+++
title = "Jeffreys Prior"
author = ["Jethro Kuan"]
slug = "jeffreys_prior"
draft = false
+++

The Jeffrey's prior is an easy-to-compute reference prior that is
invariant to transformation, used in [Bayesian Inference]({{<relref "bayesian_inference.md" >}}). If the model
only has a univariate parameter \\(\theta\\), the prior is given by:

\begin{equation}
p(\theta) \propto \sqrt{I(\theta)}
\end{equation}

where \\(I(\theta)\\) is the expected [Fisher information]({{<relref "fisher_information.md" >}}) in the model.

If \\(\mathbf{\theta}\\) is multi-dimensional, then the Jeffrey's prior is
given by:

\begin{equation}
p(\theta) \propto \sqrt{\operatorname{det}\\{l(\theta)\\}}
\end{equation}

where I is the [Fisher information matrix]({{<relref "fisher_information.md" >}}). When the number of
dimensions is large, this method becomes cumbersome. A common approach
is to obtain non-informative priors for the parameters individually,
and form the joint prior as a product of these individual priors.
