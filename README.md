# Text Flappy Bird Reinforcement Learning

## Overview
This project explores the effectiveness of two reinforcement learning algorithms—Monte Carlo (MC) and SARSA(λ)—in solving the **Text Flappy Bird (TFB)** environment. The objective is to compare their **performance, convergence speed, sensitivity to hyperparameters, and adaptability** across different environment configurations.

## Algorithms Implemented
### Monte Carlo (MC) Agent
- Implements **First-Visit MC Control** using an **ϵ-greedy policy**.
- Updates Q-values at the end of each episode.
- Uses **discounted rewards** and **step-size α** for learning.
- Provides **smooth but slow learning**, with stable convergence over multiple episodes.
- Works best when full episodes can be completed without frequent terminations.

### SARSA(λ) Agent
- Implements **TD(λ) learning** with **eligibility traces**.
- Updates Q-values at each step, improving learning speed.
- Uses an **ϵ-greedy policy** with decaying exploration rate.
- **More adaptive but highly sensitive** to hyperparameters like λ and α.
- Faster convergence but higher variance compared to Monte Carlo.

## Environment: Text Flappy Bird
This project uses **TextFlappyBird-v0**, a structured RL environment where the state representation consists of numerical values such as:
- Distance to the next pipe
- Vertical velocity
- Bird’s position

This structured representation makes it ideal for **tabular RL methods**, unlike pixel-based environments that require deep learning.

## Training Setup
- **Episodes**: 100,000
- **Evaluation Metrics**: Cumulative rewards, policy stability, and state-value functions.
- **Hyperparameters Tuned**: Learning rate (α), discount factor (γ), exploration rate (ϵ), eligibility trace decay (λ).

## Key Findings
- **MC provides stable and risk-averse learning**, but is slower.
- **SARSA(λ) learns faster but exhibits higher variance**.
- **MC generalizes better** across different environment variations (e.g., pipe gaps, width, height).
- **SARSA(λ) is more adaptive but requires careful hyperparameter tuning**.

## Performance Analysis
### Policy Differences
- **MC Agent**: Forms a **structured and predictable policy**, with clear decision boundaries between "Flap" and "Idle".
- **SARSA(λ) Agent**: Exhibits **higher variability**, making it more responsive but less stable.

### State-Value Function Differences
- **MC Agent**: Smooth, gradual updates with stable value estimates.
- **SARSA(λ) Agent**: More aggressive updates, leading to sharper peaks and fluctuations.

### Sensitivity to Environment Changes
| Environment Factor | MC Performance | SARSA(λ) Performance |
|--------------------|---------------|----------------------|
| **Height** | Stable | Gradually improves but fluctuates at extreme heights |
| **Width** | Consistent | Stronger improvements with increased width |
| **Pipe Gap** | Minimal variation | More fluctuations, especially with smaller gaps |
