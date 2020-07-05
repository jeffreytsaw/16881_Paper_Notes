# SFV: Reinforcement Leaarning of Physical Skills from Videos

This paper outlines aan approach of developing character controllers from monocular video through pose estimation and deep reinforcement learning

Traditional controllers and animations derived from motion capture data is limited by the requirement of heavily controlled sensors and environments for actors. Using monocular videos (e.g YouTube) is more widespread but it is hard to extract useful information.

Pose estimation alone is insufficient as is sensitive to inconsistencies in estimates, and fails to account for physical limitaations. RL helps refine noisy pose estimates, compensates for missing frames, and accounts for environment and physical restraints making a more robust controller

Develop better motion reconstructions that are more amenable from monocular videos and novel reinforcement learning algorithm that uses adaptive state initialization dynamically updating initial state distribution to facillitate long-term horizon reward.

Inputs a reference video and simulated character model (character + environment). Extracts poses from videos through **Pose Estimation**, uses estimataes to calculate motion trajectory that adheres to 2D/3D pose estimates and temporal consisency between frames in **Motion Reconstruction** phase, trains character to imitate reference motion by learning a policy in the  **Motion imitation** phase through deep reinforcement learning.

Pose estimator is trained according to weakly supervised approach - i.e without a ground truth 3D labels. (not really sure what weakly supervised entails, will look up later).

Pose estimator combines OpenPose 2D joint location coordinates with HMR 3D pose (parametrized by joint angles and relative axis where root is pelvis). 3D pose is learned through a encoder-decoder network that transforms image to 3D pose with only 2D pose annotations.

RL model is trained to optimize a policy that imitates motion via motion imitation objective.

Pose estimator was trained on augmented data set of regular poses with additional rotated versions of poses on range [0, 2π]







