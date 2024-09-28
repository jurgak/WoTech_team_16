## 1D Random Walk

Simulate a 1D simple random walk where at each step can be moving only up or down. How many steps ⏫  can you actually get?

```py
import numpy as np
import matplotlib.pyplot as plt
import random

def simulate_random_walk(n_steps):
    steps = np.zeros(n_steps)

    for i in range(n_steps):
        step = random.randint(0, 1) * 2 - 1  # Randomly choose to move up (1) or down (-1)
        if i == 0:
            steps[i] = step
        else:
            steps[i] = steps[i-1] + step

    return steps

# Number of steps in the random walk
n_steps = 1000
steps = simulate_random_walk(n_steps)

# Create an array of step indices
step_indices = np.arange(n_steps)

# Plotting the random walk
plt.figure(figsize=(10, 6))
plt.plot(step_indices, steps, label='Random Walk', color='red')
plt.title('1D Simple Random Walk')
plt.xlabel('Step')
plt.ylabel('Position')
plt.legend()
plt.grid(True)
plt.show()

# Calculate how many upward steps 
upward_steps = np.sum(steps > 0)

print(f"Number of upward steps: {upward_steps}")
```
![image](https://github.com/user-attachments/assets/0e305afa-0442-49a1-b034-4f13766733c8)

