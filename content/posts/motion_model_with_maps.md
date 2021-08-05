+++
title = "Motion Model With Maps"
author = ["Jethro Kuan"]
draft = false
+++

tags
: [Velocity Motion Model]({{<relref "velocity_motion_model.md#" >}}), [Odometry Motion Model]({{<relref "odometry_motion_model.md#" >}})

Often, we are given map \\(m\\) of the environment, giving us further
information about the robot pose \\(x\_t\\). In general,

\begin{equation}
  p\left(x\_{t} | u\_{t}, x\_{t-1}\right) \neq p\left(x\_{t} | u\_{t}, x\_{t-1}, m\right)
\end{equation}

And the map-based motion model should give better results. Computing
this motion model in closed form is difficult. An approximation via
factorization works well where the distance \\(x\_{t-1}\\) and \\(x\_t\\) is
small.

\begin{equation}
  p\left(x\_{t} | u\_{t}, x\_{t-1}, m\right)=\eta p\left(x\_{t} | u\_{t}, x\_{t-1}\right) p\left(x\_{t} | m\right)
\end{equation}