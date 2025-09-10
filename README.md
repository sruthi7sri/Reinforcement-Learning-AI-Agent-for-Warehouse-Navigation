# Reinforcement Learning Agent for Warehouse Navigation

This project presents a comprehensive exploration of reinforcement learning (RL) for solving a classic robotics problem: autonomous navigation in a warehouse environment. An intelligent agent is trained to efficiently navigate a grid-based warehouse, locate and retrieve a package, and deliver it to a designated drop-off location, all while avoiding obstacles. 🤖

The core of this project lies in the implementation, tuning, and comparative analysis of several fundamental RL algorithms, demonstrating their strengths and weaknesses in this specific application.

---
## 📜 Core Features

* **Customizable Warehouse Environment**: A simulated grid world that models a warehouse layout, complete with shelves (obstacles), a package pick-up location, and a delivery destination.
* **Multiple RL Algorithms**: From-scratch implementations of SARSA, Q-learning, N-step SARSA, and Double Q-learning.
* **Rigorous Hyperparameter Tuning**: A systematic approach to optimizing the learning process by tuning key hyperparameters for each algorithm.
* **In-depth Performance Analysis**: Detailed evaluation and visualization of agent performance using metrics like cumulative reward and convergence speed.

---
## 🏢 The Warehouse Environment

The agent's world is a discrete, grid-based environment that simulates the layout of a small warehouse.

* **State Space**: The state is defined by the agent's `(row, column)` coordinates and whether it is currently holding the package (0 for no, 1 for yes). This results in a state space of `grid_height * grid_width * 2`.
* **Action Space**: The agent can perform one of four discrete actions at any given time: `Up`, `Down`, `Left`, `Right`.
* **Rewards**: The reward system is designed to guide the agent's learning:
    * **+20**: Successfully delivering the package to the drop-off point.
    * **-1**: For each step taken (encourages efficiency).
    * **-5**: For bumping into a shelf or a wall (discourages invalid moves).

---
## 🧠 Algorithms Explored

This project implements and compares several cornerstone algorithms in temporal-difference (TD) learning.

### 1. SARSA (State-Action-Reward-State-Action)

SARSA is an **on-policy** TD learning algorithm. This means it learns the value of the policy it is currently following. The Q-value update for SARSA considers the action *actually taken* in the next state.

**Update Rule:**
$Q(s, a) \leftarrow Q(s, a) + \alpha [r + \gamma Q(s', a') - Q(s, a)]$

Where:
* `$\alpha$` (alpha) is the learning rate.
* `$\gamma$` (gamma) is the discount factor.
* `(s, a)` is the current state-action pair.
* `(r, s', a')` is the reward, next state, and next action.

### 2. Q-learning

Q-learning is an **off-policy** TD learning algorithm. It learns the value of the optimal policy, regardless of the agent's current actions. The Q-value update uses the maximum possible Q-value for the next state, making it more "greedy" in its updates compared to SARSA.

**Update Rule:**
$Q(s, a) \leftarrow Q(s, a) + \alpha [r + \gamma \max_{a'} Q(s', a') - Q(s, a)]$

### 3. N-step SARSA

This is an extension of SARSA that looks ahead `n` steps. Instead of updating based on a single step's reward, it accumulates rewards over `n` steps and then performs the update. This can significantly speed up the propagation of reward information, especially in environments with delayed rewards.

**Update Rule:** The update involves a multi-step return, $G$, which sums the discounted rewards over `n` steps and bootstraps the value of the state `n` steps in the future.

### 4. Double Q-learning

Standard Q-learning can suffer from **maximization bias**, where it overestimates the Q-values due to noise in the environment. Double Q-learning addresses this by decoupling the action selection from the action evaluation. It maintains two separate Q-tables, $Q^A$ and $Q^B$.

**Update Rule (for updating $Q^A$):**
1.  Select the best action $a^*$ from the next state $s'$ using $Q^A$: $a^* = \arg\max_{a'} Q^A(s', a')$
2.  Update $Q^A$ using the value of that action from $Q^B$:
    $Q^A(s, a) \leftarrow Q^A(s, a) + \alpha [r + \gamma Q^B(s', a^*) - Q^A(s, a)]$

---
## 📊 Results and Analysis

A thorough hyperparameter tuning process was conducted for each algorithm to find the optimal values for the learning rate (`alpha`), discount factor (`gamma`), and exploration rate (`epsilon`).

The key findings from the comparative analysis are:

* **Q-learning vs. SARSA**: Q-learning generally demonstrates slightly more aggressive and faster learning due to its off-policy nature, directly learning the optimal path. SARSA, being on-policy, takes a more "cautious" approach.
* **N-step SARSA**: This algorithm showed significant performance improvements over the 1-step SARSA, converging much faster. By looking further into the future, it was able to more effectively assign credit to actions that led to long-term rewards.
* **Double Q-learning**: This algorithm proved to be the most robust. By mitigating the overestimation bias of standard Q-learning, it achieved a more stable and reliable convergence to the optimal policy, ultimately yielding the best performance in terms of cumulative reward.

The notebooks contain detailed plots visualizing the learning curves (reward per episode) which clearly illustrate these performance differences.

---
## ⚙️ Dependencies and Installation

This project is built with Python 3. The primary dependencies are listed in `requirements.txt`.

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/reinforcement-learning-ai-agent-for-warehouse-navigation.git](https://github.com/your-username/reinforcement-learning-ai-agent-for-warehouse-navigation.git)
    cd reinforcement-learning-ai-agent-for-warehouse-navigation
    ```

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

---
## 🚀 Usage

The project is structured across several Jupyter notebooks within the `agent/` directory:

1.  **`agent_navigation.ipynb`**: This notebook introduces the basic environment and the implementation of the SARSA agent. It's a great starting point to understand the core mechanics.
2.  **`warehouse_logic_bonus.ipynb`**: This is the main notebook for a deep dive. It contains the implementations, hyperparameter tuning, and detailed comparative analysis of Q-learning, N-step SARSA, and Double Q-learning. Run this to see the full results and comparisons.
3.  **`visualization_bonus.ipynb`**: A supplementary notebook for visualizing the warehouse environment and the agent's path.

---
## 🔭 Future Work

* **Deep Reinforcement Learning**: Replace the tabular Q-tables with neural networks (Deep Q-Networks, DQN) to handle much larger and continuous state spaces.
* **Dynamic Environments**: Introduce dynamic elements, such as moving obstacles or changing package locations, to test the adaptability of the agents.
* **Advanced Algorithms**: Implement more modern algorithms like Proximal Policy Optimization (PPO) or Soft Actor-Critic (SAC).
* **Multi-Agent Systems**: Expand the simulation to include multiple agents operating in the same warehouse, introducing challenges of coordination and collision avoidance.

---
## 📚 References

* [1] Sutton, R. S., & Barto, A. G. (2018). *Reinforcement learning: An introduction*. MIT press.
* [2] Rummery, G. A., & Niranjan, M. (1994). *Online Q-learning using connectionist systems*. Cambridge University.
* [3] Watkins, C. J. C. H. (1999). *Learning from delayed rewards*. King's College, Cambridge.
* [4] Van Hasselt, H. (2010). Double Q-learning. In *Advances in neural information processing systems* (pp. 2613-2621).
* [5] Van Hasselt, H., Guez, A., & Silver, D. (2016). Deep Reinforcement Learning with Double Q-Learning. In *AAAI* (Vol. 30, No. 1).

## Collaborators

- Sruthisri Venkateswaran  
- Sri Sakthi Thirumagal Poovannan

## License
© 2024 Sruthisri Venkateswaran and Sri Sakthi Thirumagal Poovannan. All rights reserved.
