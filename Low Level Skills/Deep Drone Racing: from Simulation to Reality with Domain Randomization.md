# Deep Drone Racing: from Simulation to Reality with Domain Randomization

Approach uses CNNs to identify waypoints in local body-frame coordinates which are fed to a planner and tracker that generates a trajectory and corresponding motor commands.

Domain randomization makes perception system (waypoint definitions) more robust. Train on randomized values of illumination, viewpoint, gate appearence, and background.

Domain randomization helps bridge simulation and physical experiments. Policy learned in simulation has similar performance in physical system alleviating the need to train on data collected from physical systems.

Perception systems takes camera image and uses a CNN to output goal direction in local image coordinates, and desired navigation speed. Control system uses perception system's navigation goal to generate a minimum-jerk interception trajectory.

Image coordinates are back projeced along camera projection ray and the goal point is derived at a depth equal to prediction horizon d (empirically set) to convert image coordinates to 3D local frame coordiantes.

navigation speed predictions are scaled to produce desired navigation speed. 

Trajectory is computed by control system after scaling velocity and transforming image coordinates. Minimum-jerk trajectory is generated and selected. Trajectory is traacked with low-level control commands.

Training is done through imitation learning of global optimal trajectories which are generated by assuming accurate state estimates and fixed gate locations. Global traajectory is determined using minimum-snap trajectory implementation. This involves generating set of waypoints (center of gaates) to pass through, maximum velocity to achieve, and constraints on thrus and body rates (roll and pitch).

Expert polilcy: Desired goal is point on global trajectory d away from quadcopter position. This position is projeced onto image plane of camera to generate image coordinates used to train perception system. Desired velocity is the velocity at position on reference trajectory closest to quadcopter position normalized by maximum speed during trajectory. These 2 values are generated and used to train perception system.  See image below.

![]()

Data was collected by calculating desired position and velocity from camera images from a dataset of state estimates and corresponding camera images. 

In simulation, expert policy flies for a period of time to generate data and train network. Network then predicts actions until quadcopter position is margin ε away from global trajectory. When this occurs, global trajectory takes over and the resulting flight is used to train network againn. If network performs well on current margin, m argin is increased until network can complete lap without expert policy.

Real data was generated by carrying quadcopter around track and generating training samples according to expert polilcy.

Training is done via MSE loss on both navigation goal predictions and velocity. This is difference in output from network and output of exper policy for a given camera image.

Generalization is achieved by training network on multiple track layouts, i.e generating multiple tracks by moving gates, computing new global trajectory, collecting expert policy data. Network is trained jointly across all the track layout data. Training data in experiments was collected by changing location of a single gate, but network was able to generalize to any gate.

Advantage of separate perception-control modules allows for perception module to be trained primarily in simulation allowing for a more diverse training set and similar performance on physical systems. 

Visual scene randomization randomizes gate shape, gate texture, background texture, ambient lighting to environment, and uses these randomizes environments to collect expert policy data to train network to make more robust.

Perception network outputs of goal position and desired velocity are used to compute interception trajectories. Trajectories are defined by start state (current position, velocity, acceleration), execution time (defined by desired velocity) and end state (unconstrained velocity, acceleraation, and goal position fed by perception network).

Projection horizon d determines smoothness of flight. Smaller d means less deviation from global trajectory and allows for more agile manoeuvre. Larger d allows for smoother flights on straightaways.

Note goal positions during training are calculated by projecting quadcopter position to global trajectory along some prediction horizon (d-train). Test time goal positions have no global trajectory, so are calculated by back-projecting perception network image coordinates through camera ray by some planning length (d-test).

d-train is selected based on distances to last and next gates and a minimum prediction horizon d-min. (d-train = max(d-min, min(distance to last gate, distance to next gate)))

d-test planning length is selected based on empirical values d-min, d-max, and a weighted velocity factor, wv, (from perception network). Goal is to maintain smooth flight while allowing for agile maneouvres if necesssary. (d-test = min(d-max, max(d-min, wv)))

Perception system trained only on simulalted data is more robust to differences in illlumination and distractors than one traained with real handheld data.

Issues with magnification of errors through pipeline, as well as actions in ambiguous environments (multiple gates/no gates visible) present future issues. Using a Sim2Real policy, background cues cannot inform decisions in ambiguous cases as they could if policy was trained on real data.

Paper: [Deep Drone Racing: from Simulation to Reality with Domain Randomization](https://arxiv.org/pdf/1905.09727.pdf). Approach presented here is interesting, in terms of formulating goal location and speed in terms of a global trajectory and a projecion horizon. Still unsure about how back-projecting image coordinates through camera ray works, but oh well. A lot of the control schemes and trajectory calculations was not elaborated on. Most of the focus was formulating a goal location and velocity, creating a trajectory, but not much on how this is applied to drone control. The dynamic projection horizon was a cool idea.
