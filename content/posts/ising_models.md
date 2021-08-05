+++
title = "Ising Models"
author = ["Jethro Kuan"]
tags = ["machine-learning"]
draft = false
+++

An Ising model is an array of spins (atoms that can take states \\(\pm
1\\)) that are magnetically coupled to each other. If one spin is, say
$+1, is energetically favourable for its immediate neighbours to be in
the same state.

Let the state \\(\mathbb{x}\\) of an Ising model with \\(N\\) spins be a
vector in which each component \\(x\_n\\) takes values \\(+1\\) and \\(-1\\). If
two spins \\(m\\) and \\(n\\) are neighbours, we say \\((m, n) \in \mathcal{N}\\).
The coupling between neighbouring spins is \\(J\\). We define \\(J\_{mn} = J\\)
if \\(m\\) and \\(n\\) are neighbours, and \\(J\_{mn} = 0\\) otherwise. The energy
of a state \\(\mathbf{x}\\) is:

\begin{equation}
  E(\mathbb{x}| J, H) = - \left[ \frac{1}{2} \sum\_{m,n}
    J\_{mn}x\_{m}x\_{n} + \sum\_{n} H x\_{n} \right]
\end{equation}

where \\(H\\) is the applied field. The probability that the state is
\\(\mathbb{x}\\) is:

\begin{equation}
P(\mathbb{x} | J, H) = \frac{1}{Z(\beta, J, H)} \textrm{exp} \left[ -
  -\beta E(\mathbb{x}; J, H) \right]
\end{equation}

where \\(\beta = \frac{1}{k\_B T}\\), \\(k\_B\\) is the Boltzmann's constant,
and:

\begin{equation}
  Z(\beta, J, H) = \sum\_{\mathbb{x}} \textrm{exp} \left[ - \beta
    E(\mathbb{x}; J,H) \right]
\end{equation}

The Ising model is also an example of a Markov Random Field (MRF). We
create a graph in the form of a 2D or 3D lattice, and connect
neighbouring variables. We can define the following clique potential:

\begin{equation}
  \phi\_{st} (y\_s, y\_t) = \begin{pmatrix}
    e^{w\_{st}} & e^{-w\_{st}} \\\\\\
    e^{-w\_{st}} & e^{w\_{st}}
  \end{pmatrix}
\end{equation}

Here \\(w\_{st}\\) is the coupling strength between nodes \\(s\\) and \\(t\\). If
two nodes are not connected, \\(w\_{st} = 0\\). The weight matrix
\\(\mathbb{W}\\) is symmetric: \\(w\_{st} = w\_{ts}\\). All edges have the same
strength \\(J\\), where \\(w\_{st} \ne 0\\).

The Ising model is analogous to the Gaussian graphical models. First,
assuming \\(y\_t \in \\{-1, +1\\}\\), we can write the unnormalized log
probability of an Ising model as follows:

\begin{equation}
  \log \tilde{p}(\mathbb{y}) = - \sum\_{s \sim t} y\_s w\_{st} y\_t +
  \sum\_{s}b\_s y\_s = -
  \frac{1}{2}\mathbb{y}^T \mathbb{W} \mathbb{y} + \mathbb{b}^T \mathbb{y}
\end{equation}

where \\(\theta = (\mathbb{W}, \mathbb{b})\\), and \\(\mathbb{b}\\) is the
bias term, corresponding to the local fields. If we define:

\begin{equation}
  \mu = - \frac{1}{2}\mathbb{\Sigma}^{-1}\mathbb{b},
  \mathbb{\Sigma}^{-1} = - \mathbb{W}, c = \frac{1}{2}\mathbb{\mu}^T \mathbb{\Sigma}^{-1}\mu
\end{equation}

we can rewrite this in a form that looks similar to a Gaussian:

\begin{equation}
\log \tilde{p}(\mathbb{y}) = - \frac{1}{2}(\mathbb{y} -
\mathbb{\mu})^T \Sigma ^{-1} (\mathbb{y} - \mathbb{\mu}) + c
\end{equation}