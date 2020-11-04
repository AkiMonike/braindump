+++
title = "Robot Localization"
author = ["Jethro Kuan"]
draft = false
+++

Mobile robot localization is the problem of estimating the robots
coordinates in an external reference frame from sensor data, relative
to a given map of the environment.

The robot's momentary estimate (belief) is represented by a
probability density function over the space of all locations. A
uniform distribution as prior represents maximal uncertainty.

Localization can be seen as a problem of coordinate transformation.
Maps are described in the global coordinate system, independent of the
robot's pose. Localization is the process of establishing
correspondence between the map coordinate system and the robot's local
coordinate system.

Pose often cannot be sensed directly, and has to be inferred from
data. A single sensor measurement is usually insufficient, and
integrating data over time is required to determine the pose.

## Taxonomy {#taxonomy}

### Local vs Global localization {#local-vs-global-localization}

position tracking
: initial robot pose is known. Localization is
achieved by accommodating the noise in robot motion. The problem is
local, since the uncertainty is local and confined to the region
near the robot's true pose.

global localization
: initial robot pose is unknown. Robot is
initially placed somewhere in its environment, but it lacks
knowledge of where it is.

kidnapped robot problem
: During operation, the robot can get
kidnapped and teleported to some other location. The robot might
believe it knows where it is, while it does not.

### Static vs Dynamic Environment {#static-vs-dynamic-environment}

static environment
: only variable quantity is the robot's pose.
Other objects remain at the same location forever.

dynamic environment
: there exists objects whose location or
configuration may change over time.

### Passive vs Active Approaches {#passive-vs-active-approaches}

passive localization
: localization module only observes the robot
operating: the robot is controlled via other means.

active localization
: control the robot as to minimize the
localization error or costs arising from moving a poorly localized
robot into a hazardous place.

## Summary {#summary}

{{< figure src="/ox-hugo/screenshot2019-12-05_18-15-41_.png" caption="Figure 1: Comparisons between different Markov localization techniques" >}}
