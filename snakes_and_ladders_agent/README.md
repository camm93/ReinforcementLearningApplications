# 🎲 Reinforcement Learning Agent for Modified Snakes and Ladders

This project implements a reinforcement learning (RL) agent trained using Q-Learning to solve a simplified and modified version of the classic board game **Snakes and Ladders**. The agent learns how to reach a victory cell while avoiding traps, leveraging feedback from the environment through rewards and penalties.

---

## 🧠 Problem Setup

- **Board**: A static 10x10 grid (100 cells).
- **Agent**: A single player that can move **left** or **right** only.
- **Special Cells**:
  - 🟥 **Traps**: End the game with a negative reward.
  - 🟩 **Victory Cells**: End the game with a positive reward.
  - 🔵 **Ladders**: Automatically transport the agent up the board.
  - 🟠 **Slides (Snakes)**: Automatically transport the agent down the board.

The goal of the agent is to reach a victory cell while minimizing punishment from traps or unnecessary steps.

---

## 🧩 Environment (`SnakesLadders` Class)

The board environment is defined in a custom Python class with the following core features:

- `nrows`, `ncols`: Grid size.
- `state`: Current agent position.
- `sinks`, `victories`: Coordinates for traps and winning cells.
- `snakes`, `ladders`: Transition rules for automatic movement.

### Key Methods:

- `get_possible_actions()`: Returns `{left, right}`.
- `do_action()`: Moves the agent based on chosen action.
- `is_terminal()`: Checks if current state is terminal.
- `reset()`: Resets the board for a new episode.

---

## 🧠 Agent (`QLearning` Class)

Implements Q-Learning to train an agent on the environment.

### Parameters:

- `epsilon = 0.99`: High initial exploration.
- `gamma = 0.95`: Future reward discount.
- `alpha = 0.55`: Learning rate.
- `episodes = 50,000`: Total training runs.

### Rewards:

- `VICTORY_REWARD = +100`
- `LOSS_REWARD = -15`
- `STEP_REWARD = -1`

### Key Methods:

- `choose_action()`: Uses epsilon-greedy strategy.
- `update_values()`: Updates Q-table.
- `run()`: Executes episodes.
- `test_performance()`: Displays learned optimal policy.

---

## 🧪 Training & Results

- Trained using CPU on Google Colab.
- 50,000 episodes took ~10 minutes.
- The agent starts in the bottom-left cell and learns the best policy to reach a victory cell.
- Final test run (with `epsilon=0`) shows the agent consistently reaches terminal victory state instead of wandering or falling into traps.

---

## 📊 Observations

- **Reward design** was critical: Too high a penalty discouraged exploration, too low a reward failed to motivate the agent.
- **Hyperparameters** significantly influenced learning. High `epsilon` at the start enabled sufficient exploration; high `gamma` encouraged long-term strategy.
- **Simplicity of actions (left/right)** did not limit learning. Despite limited choices, the agent learned optimal paths.

---

## 🚧 Limitations and Future Work

- Board is static and deterministic; could add randomness or a second agent for complexity.
- Consider expanding to larger boards, more rules (turn limits, intermediate rewards).
- Could evaluate Deep Q-Learning (DQN) for scaling to more complex action/state spaces.

---

## ✅ Conclusion

This project demonstrates how Q-Learning can solve non-trivial sequential decision-making tasks, even in environments with few actions but complex transitions. The agent successfully learned to avoid traps and reach victory by optimizing a reward-based policy.

---

**Contributors**
- Cristian Murillo
- Diego Pedreros
