# Throwing Environment Simulation

## Overview
This project implements a throwing environment simulation using a two-link robotic arm. The environment models physics-based interactions, reinforcement learning (RL) training, and visualization of throwing dynamics.

## Features
- **Physics-Based Simulation:** Simulates the kinematics and dynamics of a two-link robotic arm.
- **Reinforcement Learning Support:** Implements Q-learning-based training.
- **Visualization Tools:** Provides real-time plotting and animation of the robotic arm and thrown object.
- **Customizable Parameters:** Allows modification of arm lengths, gravity, reward structures, and more.

## Dependencies
Ensure you have the following Python libraries installed:

```bash
pip install numpy matplotlib tqdm
```

## Usage
### Initialization
Create an instance of the `ThrowingEnvironmentBase` class by specifying:
- `file_name`: Unique identifier for saving/loading data.
- `q_size`: Size of the Q-table for reinforcement learning.

```python
from throwing_environment import ThrowingEnvironmentBase

env = ThrowingEnvironmentBase(file_name="2023-2024", q_size=[10, 10, 10, 10])
```
The Q-table is a lookup table where the algorithm stores the estimated rewards for different actions and states. In this case, the size [10, 10, 10, 10] suggests a 4D table, meaning there are four state variables, each discretized into 10 bins.

### Running the Simulation
To reset and visualize the environment:

```python
env.reset()
env.plot_state()
```

To run a full training session:

```python
env.train(1000)  # Train for 1000 epochs
env.summary()
```
- Runs 1000 training iterations (epochs) to optimize the throwing strategy.
- Each epoch:
  - Selects an action based on the Q-table (or randomly at first).
  - Simulates the result of the action (arm movement & object throw).
  - Updates the Q-table based on the reward received.
  - Repeats until the model improves its throwing accuracy.


To animate the simulation:

```python
env.plot_simulate(duration=5, reset=True)
```
- Creates an animation of the robotic arm performing a throw.
- duration=5 means the animation will run for 5 seconds.
- reset=True ensures that the environment starts fresh before the animation.

## Future Improvements
- Implement deep reinforcement learning (DQN or PPO) for better training.
- Extend the environment for multi-objective tasks.
- Improve visualization and UI elements.


