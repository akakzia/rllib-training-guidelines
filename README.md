# RLlib Training Guidelines

The objective of this training is to gain knowledge of [RLlib](https://docs.ray.io/en/latest/rllib/index.html), a widely used open source library for reinforcement learning (RL). RLlib is used in many projects at InstaDeep thanks to its production-level support, maintainability and relatively easy usage.

Throughout this training, your task is to solve the [Go To Door](https://minigrid.farama.org/environments/minigrid/GoToDoorEnv/) problem with the Soft Actor-Critic ([SAC](https://arxiv.org/abs/1801.01290)) algorithm with [discrete actions](https://arxiv.org/abs/1910.07207). This is a simply goal-conditioned problem where you need to train a single policy to reach several different goals. 

To accomplish this mission, you will need to **customize many components in RLlib, augment your solution with connectors, design custom a custom evaluation protocol and launch experiments**. We have broken this exercise into several steps, which can be found in the issues directory. The main steps are outlined below: 

+ Setup RLlib and Minigrid.
+ Create your first training script.
+ Create a custom RLModule for discrete actions SAC. 
+ Implement your custom environment wrapper.
+ Implement Hindsight Experience Replay through Learner Pipeline Connector. 
+ Implement your custom evaluation protocol. 
+ Log metrics to Neptune. 
+ Perform hyper-parameter tuning 

### Contributing

- [x] Create repo.
- [x] Setup uv.
- [x] Setup environment.
- [ ] Setup RLlib.
- [ ] Setup Training Pipeline.