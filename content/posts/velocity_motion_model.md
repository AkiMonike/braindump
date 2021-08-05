+++
title = "Velocity Motion Model"
author = ["Jethro Kuan"]
draft = false
+++

tags
: [Odometry Motion Model]({{<relref "odometry_motion_model.md#" >}}), [Motion Model With Maps]({{<relref "motion_model_with_maps.md#" >}})

The velocity motion model assumes that the robot is controlled through
2 velocities: rotational and translational velocity:

\begin{equation}
  u\_{t}=\left(\begin{array}{l}{v\_{t}} \\ {\omega\_{t}}\end{array}\right)
\end{equation}

A sampling algorithm generates a random pose according to the
distribution \\(p(x\_t| u\_t, x\_{t-1})\\), and perturbs it with the noise,
drawn from the error parameters of the kinematic motion model.

\begin{equation}
  \left(\begin{array}{c}{\hat{v}} \\ {\hat{\omega}}\end{array}\right)=\left(\begin{array}{c}{v} \\ {\omega}\end{array}\right)+\left(\begin{array}{c}{\varepsilon\_{\alpha\_{1}|v|+\alpha\_{2}|\omega|}} \\ {\varepsilon\_{\alpha\_{3}|v|+\alpha\_{4}|\omega|}}\end{array}\right)
\end{equation}