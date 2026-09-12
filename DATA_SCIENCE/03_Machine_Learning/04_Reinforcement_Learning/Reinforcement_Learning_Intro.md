# Reinforcement Learning (Intro)

**Folder:** [[🎮 Reinforcement Learning]] · **Topic:** #ml #reinforcement

## What it is
An agent learns by **doing**: take an action in a state, get a reward, update behavior. Classic algorithms: **Q-Learning**, **SARSA**, **Policy Gradient**, **DQN**, **PPO**.

## Key idea
**Exploration vs exploitation** — try new actions to learn, but also use what you already know to earn reward. The whole field balances those two.

## Python
```python
# Tabular Q-learning on a 1-D walk: state 0..4, goal at 4
import numpy as np, random
Q = np.zeros((5, 2))               # 5 states, 2 actions: 0=left, 1=right
alpha, gamma, eps = 0.1, 0.9, 0.1
for episode in range(500):
    s = 0
    while s != 4:
        a = random.randint(0, 1) if random.random() < eps else int(np.argmax(Q[s]))
        s_new = max(0, min(4, s + (1 if a == 1 else -1)))
        r = 1 if s_new == 4 else 0
        Q[s, a] += alpha * (r + gamma * Q[s_new].max() - Q[s, a])
        s = s_new
print(Q.round(2))                  # right-action values should grow toward goal
```

## Related
- [[Supervised vs Unsupervised]]
- [[Neural_Networks_Intro]] (deep RL)
- [[Hyperparameter_Tuning]]
