Inspired by [Daniel Takeshi][1].

This repo contains notes for the papers that are apart of the course [16-881 Deep Reinforcement Learning for Robotics][2]. Papers here are arranged by theme, and for the most part will have 2 papers associated with it: one on a deep reinforcement learning approach (marked with (D) ), the other on a different approach that may or may not use reinforcement learning (marked with (R) ). For reference, these notes assume the reader has a basic grasp of RL approaches, more specificallly, policy gradients, as action spaces in robotics are general non-discrete. My goal through reading these papers is to gain insight into reinforcement learning applications to robotics and hopefully inspire me to do research in the future. 

Contents:
- [Low Level Skills](#low-level-skills)
  - [Bipedal Locomotion](#bipedal-locomotion)
  - [Robot Acrobatics](#robot-acrobatics)
  - [Flight / Aerial Robotics](#flight--aerial-robotics)
  - [Drifting](#drifting)
  - [Throwing / Catching](#throwing--catching)
  - [Grasping](#grasping)
  - [In-hand Manipulation](#in-hand-manipulation)
  - [Sim2Real Transfer](#sim2real-transfer)
  - [Reward Functions](#reward-functions)
- [High Level Reasoning](#high-level-reasoning)
  - [Autonomous Driving](#autonomous-driving)
  - [Navigation](#navigation)
  - [Safety](#safety)
  - [Multi-object Manipulation](#multi-object-manipulation)
  - [Tool Use](#tool-use)
  - [Long-horizon Tasks / Reasoning / Planning](#long-horizon-tasks--reasoning--planning)

# Low Level Skills

## Bipedal Locomotion
- [DeepLoco: Dynamic Locomotion Skills Using Hierarchical Deep Reinforcement Learning (D)](https://github.com/jeffreytsaw/16881_Paper_Notes/blob/master/Low%20Level%20Skills/DeepLoco:%20Dynamic%20Locomotion%20Skills%20Using%20Hierarchical%20Deep%20Reinforcement%20Learning.md)
- [Experiments in Balance with a 3D One-Legged Hopping Machine (R)](https://github.com/jeffreytsaw/16881_Paper_Notes/blob/master/Low%20Level%20Skills/Experiments%20in%20Balance%20with%20a%203D%20One-Legged%20Hopping%20Machine.md)

## Robot Acrobatics
- [Control of a Biped Somersault in 3D (R)](https://github.com/jeffreytsaw/16881_Paper_Notes/blob/master/Low%20Level%20Skills/Control%20of%20a%20Biped%20Somersault%20in%203D.md) 
- [SFV: Reinforcement Learning of Physical Skills from Videos](https://github.com/jeffreytsaw/16881_Paper_Notes/blob/master/Low%20Level%20Skills/SFV:%20Reinforcement%20Learning%20of%20Physical%20Skills%20from%20Videos.md)

## Flight / Aerial Robotics
- Beauty and the Beast: Optimal Methods Meet Learning for Drone Racing
- Deep Drone Racing: From Simulation to Reality with Domain Randomization

## Drifting
- Autonomous Drifting using Simulation-Aided Reinforcement Learning
- Information Theoretic MPC for Model-Based Reinforcement Learning
- Toward Automated Vehicle Control Beyond the Stability Limits: Drifting Along a General Path
- Locally Weighted Regression Pseudo-Rehearsal for Online Learning of Vehicle Dynamics

## Throwing / Catching
- Catching objects in flight
- TossingBot: Learning to Throw Arbitrary Objects

## Grasping
- 6-DOF GraspNet: Variational Grasp Generation for Object Manipulation
- Quantile QT-Opt for Risk-Aware Vision-Based Robotic Grasping
- Multi-Modal Geometric Learning for Grasping and Manipulation
- MAT - Multi-Fingered Adaptive Tactile Grasping via Deep Reinforcement Learning

## In-hand Manipulation
- Relaxed-Rigidity Constraints: In-Grasp Manipulation using Purely Kinematic Trajectory Optimization
- Deep Dynamics Models for Learning Dexterous Manipulation
- Extrinsic Dexterity: In-Hand Manipulation with External Forces
- Solving Rubik's Cube with a Robot Hand

## Sim2Real Transfer
- Closing the Sim-to-Real Loop: Adapting Simulation Randomization with Real World Experience
- Learning Agile and Dynamic Motor Skills for Legged Robots
- TuneNet: One-Shot Residual Tuning for System Identification and Sim-to-Real Robot Task Transfer
- Learning Locomotion Skills for Cassie: Iterative Design and Sim-to-Real
- Push-Net: Deep Planar Pushing for Objects with Unknown Physical Properties
- DensePhysNet: Learning Dense Physical Object Representations via Multi-step Dynamic Interactions

## Reward Functions
- Learning Robot Objectives from Physical Human Interaction
- Deep Reinforcement Learning from Human Preferences

# High Level Reasoning

## Autonomous Driving
- ChauffeurNet: Learning to Drive by Imitating the Best and Synthesizing the Worst
- Learning by Cheating

## Navigation
- Learning over Subgoals for Efficient Navigation of Structured, Unknown Environments
- Visual Semantic Planning using Deep Successor Representations
- Efficient Trajectory Planning for High Speed Flight in Unknown Environments
- Visual Semantic Navigation using Scene Priors

## Safety
- Safe Exploration for Interactive Machine Learning
- Safe Exploration in Continuous Action Spaces

## Multi-object Manipulation
- Neural Task Graphs: Generalizing to Unseen Tasks from a Single Video Demonstration
- Learning to Manipulate Object Collections Using Grounded State Representations

## Tool Use
- KETO: Learning Keypoint Representations for  Tool Manipulation
- Improvisation through Physical Understanding: Using Novel Objects as Tools with Visual Foresight

## Long-horizon Tasks / Reasoning / Planning
- Dream to Control: Learning Behaviors by Latent Imagination
- Relay Policy Learning: Solving Long-Horizon Tasks via Imitation and Reinforcement Learning
- Differentiable Physics and Stable Modes for Tool-Use and Manipulation Planning
- Learning Robotic Manipulation through Visual Planning and Acting














[1]: https://github.com/DanielTakeshi/Paper_Notes
[2]: https://sites.google.com/view/16-881-cmu/home
