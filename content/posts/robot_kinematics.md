+++
title = "Robot Kinematics"
author = ["Jethro Kuan"]
draft = false
+++

tags
: [Velocity Motion Model]({{<relref "velocity_motion_model.md#" >}}), [Odometry Motion Model]({{<relref "odometry_motion_model.md#" >}})

Kinematics is the calculus describing the effect of control actions on
the configuration of the robot. The configuration of a rigid mobile
robot is commonly described by 6 variables relative to an external
coordinate frame:

-   three Cartesian coordinates
-   three Euler angles (roll, pitch, yaw)

The robot's pose comprises its two-dimensional planar coordinates
relative to an external coordinate frame, along with its angular
orientation:

\begin{equation}
  \left(\begin{array}{l}{x} \\ {y} \\ {\theta}\end{array}\right)
\end{equation}

{{< figure src="/ox-hugo/screenshot2019-12-01_21-26-36_.png" caption="Figure 1: Robot pose" >}}

The motion model plays the role of the state transition model in
mobile robotics. This model is the conditional density:

\begin{equation}
  p(x\_t | u\_t, x\_{t-1})
\end{equation}

where \\(x\_t\\) and \\(x\_{t-1}\\) are both robot poses, and \\(u\_t\\) is the
motion command. In implementations, \\(u\_t\\) is sometimes provided by a
robot's odometry.

Odometry models are generally more accurate than velocity models,
because most commercial robots do not execute velocity commands with
the level of accuracy that can be obtained by measuring the revolution
of the robot's wheels. The downside is that odometry is obtained
after-the-fact, meaning it cannot be used for motion planning. Hence,
odometry models are used for state estimation, while velocity models
for motion planning.