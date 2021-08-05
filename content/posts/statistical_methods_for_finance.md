+++
title = "Statistical Methods for Finance"
author = ["Jethro Kuan"]
draft = false
+++

tags
: [Finance]({{<relref "finance.md#" >}})


## Returns {#returns}

Net Returns:

\begin{equation}
R\_t = \frac{P\_t}{P\_{t-1}} - 1 = \frac{P\_t - P\_{t-1}}{P\_{t-1}}
\end{equation}

\\(R\_t \ge -1\\): a 100% loss occurs if the asset becomes totally
worthless.

Gross Returns:

\begin{equation}
  \frac{P\_t}{P\_{t-1}} = 1 + R\_t
\end{equation}

The gross return over the most recent \\(k\\) periods is:

\begin{equation}
  1 + R\_t(k) = \frac{P\_t}{P\_{t-k}} = (1 + R\_t)\dots (1 + R\_{t-k+1})
\end{equation}

Log Returns:

\begin{equation}
  r\_t = \log (1 + R\_t) = \log \frac{P\_t}{P\_{t-1}} = p\_t - p\_{t-1}
\end{equation}

\begin{equation}
r\_t(k) = r\_t + r\_{t-1} + \dots + r\_{t-k+1}
\end{equation}

log returns are similar for daily returns, less similar for yearly
returns, and  not necessarily similar for multi-year returns.


### Random Walk Model {#random-walk-model}

In the random walk model, single-period log returns are assumed to be
independent:

\begin{align} \label{eq:rw}
  1 + R\_t(k) &= (1 + R\_t)\dots(1 + R\_{t-k+1}) \\\\\\
             &= \textrm{exp}(r\_t) \dots \textrm{exp}(r\_{t-k+1}) \\\\\\
             &= \textrm{exp}(r\_t + \dots + r\_{t-k+1})
\end{align}

It is also sometimes assumed that log returns are \\(N(\mu,\sigma^2)\\)
for some constant mean and variance. Then \\(k\\) period log returns are
\\(N(k\mu, k\sigma^2)\\).


### Geometric Random Walks {#geometric-random-walks}

From [eq:rw](#eq:rw), we have that

\begin{equation}
  \frac{P\_t}{P\_{t-k}} = 1 + R\_t(k) = \textrm{exp}(r\_t + \dots + r\_{t-k+1})
\end{equation}

A process whose logarithm is a random walk is called a geometric
random walk. If \\(r\_1\\), \\(r\_2\\), \\(\dots\\) are i.i.d \\(N(\mu, \sigma^2)\\),
then \\(P\_t\\) is lognormal for all \\(t\\) and the process is a lognormal
geometric random walk. \\(\mu\\) is called the log-mean, and \\(\sigma^2\\)
the log-standard deviation of thet lognormal distribution of
\\(exp(r\_t)\\).


### Validity of the Random Walk Model {#validity-of-the-random-walk-model}

In the lognormal geometric random walk model we assume that:

1.  log returns are normally distributed
2.  log returns are mutually independent