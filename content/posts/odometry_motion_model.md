+++
title = "Odometry Motion Model"
author = ["Jethro Kuan"]
draft = false
+++

The odometry model uses the relative information of the robot's
internal odometry. While both the [velocity motion model]({{<relref "velocity_motion_model.md#" >}}) and the
odometry motion model suffer from drift and slippage, the velocity
motion model additionally suffers from the mismatch between the actual
motion controller and the mathematical model. Odometry information are
only available in retrospect, making the model unusable for planning.