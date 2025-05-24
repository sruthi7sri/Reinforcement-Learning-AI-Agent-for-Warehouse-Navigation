# Reinforcement Learning AI Agent for Warehouse Navigation

## Overview
This project features a reinforcement learning (RL) simulation where an AI agent navigates a warehouse filled with dynamic obstacles, black holes, fuel cells, and collectible items to reach a destination. It also includes enhanced visualizations and a bonus logic for more complex layouts.

## Methodology

### Agent Navigation (Core RL Logic)
- Framework: Implemented using a state-action-reward-based logic.
- Map Representation: Grid-world setup representing different objects as tiles.
- Rewards System: Penalty for hitting obstacles, reward for collecting items and reaching the goal.
- Agent Behavior: Learns optimal path through trial-and-error reward feedback.

### Bonus: Warehouse Logic
- Added advanced map traversal strategies.
- Handles complex, obstacle-heavy maps.

### Bonus: Visualization

- Graphical representation using matplotlib, PIL, and sprites.
- Animated agent states: idle, moving, interacting with objects.

## Real-World Applications
- Warehouse Automation: AI agents simulating autonomous robots in logistics.
- Pathfinding Algorithms: Use in robotics, games, and drone navigation.
- Reinforcement Learning Education: Easy-to-follow simulation for RL fundamentals.


## Technology Comparison

| Component  | Chosen Technology                          | Alternatives                        | Rationale                                                             |
|------------|--------------------------------------------|-------------------------------------|-----------------------------------------------------------------------|
| RL Algorithm  | Custom grid-based reward system | Q-Learning, SARSA      | Simple, illustrative, fits the limited-scope environment  |
| Visualization | Matplotlib + PIL + custom sprites    | Pygame, OpenCV    | Easy integration with notebooks and interpretable outputs|



## File Structure
```bash
Reinforcement-Learning-AI-Agent-Warehouse-Navigation/
├── agent/
│   ├── agent_navigation.ipynb
│   ├── warehouse_logic_bonus.ipynb
│   └── visualization_bonus.ipynb
├── assets/
│   ├── agent_idle.png
│   ├── agent_moving.png
│   ├── background.jpg
│   ├── black_hole.png
│   ├── destination.png
│   ├── fuel_cell.png
│   └── star_fragment.png
├── README.md
└── requirements.txt
```

### What each file does

#### agent/
- agent_navigation.ipynb: Main logic for the RL agent to learn and find the optimal path.
- warehouse_logic_bonus.ipynb: Additional navigation logic to handle more complex warehouse maps.
- visualization_bonus.ipynb: Animates agent movements and interactions using sprites.

#### assets/
- Image files (*.png, *.jpg): Used for visualizing agent states, environment tiles, and game objects.

#### Top-Level
- README.md: Documentation and usage instructions.
- requirements.txt: Python libraries needed to run the notebooks.

## Installation & Usage
### Clone the Repository
```bash
git clone https://github.com/sruthi7sri/Reinforcement-Learning-AI-Agent-for-Warehouse-Navigation.git
cd Reinforcement-Learning-AI-Agent-for-Warehouse-Navigation
```
### Create & Activate Virtual Environment
```bash
python -m venv venv
source venv/bin/activate   # macOS/Linux
venv\Scripts\activate      # Windows
```

### Install Dependencies
```bash
pip install -r requirements.txt
```

### Run RL Simulation Notebooks:
Open Jupyter and run the notebooks inside the `agent/` folder.

## Dependencies:
numpy>=1.19.5
matplotlib>=3.3.2
opencv-python>=4.5.1
Pillow>=8.0.1
jupyter>=1.0.0

## Project Goals
- Build an AI agent that learns to navigate complex warehouse environments.
- Integrate visual representations to demonstrate real-time decisions.
- Support more sophisticated layouts through modular logic.
- Provide a learning tool to demonstrate key reinforcement learning principles.

## License
© 2024 Sruthisri. All rights reserved.
