# Implement a Simple Rollout script with a Random Policy

In this step, you will start by populating your repository with the first script. Create a folder named `scripts` in the root of your repository. Add a `run_random_agent.py` script to it. 

## 1. Create an environment with `FetchReach-v4` tag. Use `gymnasium`'s factory function to do so. 
‼️ Make sure that the environment you created uses dense rewards. 

‼️ You need to make sure that gymnasium_robotics is imported. Otherwise, make sure you manually register the environment. 

## 2. Set the number of steps you want your environment to run to 100. Implement an interaction loop where actions are directly sampled from the action space. 

## 3. Include a mechanism to time the environment and count the number of steps it takes per second. 

Why measure steps per second in Reinforcement Learning?

When training RL agents, the environment is often the computational bottleneck, not the learning algorithm. Knowing how fast your environment can generate experience (**steps/sec**) has direct implications:

---

### Training speed and feasibility

RL agents typically require millions of environment steps to learn.

**Example: If your algorithm needs 10 million steps:**

- At **10,000 steps/sec**, that’s ~17 minutes.  
- At **100 steps/sec**, that’s ~1 day.  

Measuring steps/sec gives you an estimate of how long training will take, and whether it’s feasible on your machine.

---

### Choice of environment

- Some environments (like **Atari**) can run very fast, generating huge amounts of data quickly.  
- Physics-based environments (like **MuJoCo robotics tasks**) are slower, but more realistic.  

Benchmarking tells you whether an environment is practical for your project.

---

### Hardware considerations

- Timing reveals whether your bottleneck is **CPU, GPU, or MuJoCo rendering**.  
- If simulation is too slow, you might need **parallel environments** (`SubprocVectorEnv`, `AsyncVectorEnv`) or even a **cluster**.  
- For MuJoCo, disabling rendering can improve throughput drastically.

---

### Algorithm design

- Some RL algorithms (e.g., **DQN, PPO, SAC**) interact differently with simulation cost.  
- Algorithms that use **replay buffers** (off-policy methods like DDPG or SAC) can reuse past experience, making them less sensitive to slow environments.  
- **On-policy algorithms** (PPO, A2C) require fresh samples each update, so slow environments directly slow down learning.

---

### Reproducibility and scaling

- Timing helps you compare runs across machines, or see how scaling to multiple environments (**vectorized simulation**) improves throughput.  
- For researchers, reporting **steps/sec** makes experiments reproducible.

Timing helps you compare runs across machines, or see how scaling to multiple envs (vectorized simulation) improves throughput.

For researchers, reporting steps/sec makes experiments reproducible.

👉 Takeaway:
Measuring steps per second is not just a technical curiosity. It directly affects how long training takes, what environments and algorithms are feasible, and how reproducible your results are.