## COIN TOSS
Design a simulation where you toss two coins simultaneously. Record the possible outcomes (heads or tails for each coin) and run the simulation for multiple trials (e.g., 100, 500, or 1000 tosses). After collecting the data:

1.Calculate the probabilities of each outcome (HH, HT, TH, TT).

2.Visualize the results using a bar chart or pie chart to represent the frequencies and probabilities of each outcome.

3.Analyze whether the results align with the expected theoretical probabilities.

```py
import numpy as np
import matplotlib.pyplot as plt
from collections import Counter

# Two Coins toss simulation
def simulate_coin_tosses(n_trials):
    outcomes =[]
    for _ in range(n_trials):
        coin_toss1 = np.random.choice(['H', 'T'])
        coin_toss2 = np.random.choice(['H', 'T'])
        outcomes.append((coin_toss1 + coin_toss2))

    return outcomes

# Run the simulation for multiple trials

trial_sets = [100, 500, 1000] #
results = {}

for n_trials in trial_sets:
    outcomes = simulate_coin_tosses(n_trials)
    outcome_counts = Counter(outcomes)
    total_outcomes = sum(outcome_counts.values())
    probabilities = {outcome: count / total_outcomes for outcome, count in outcome_counts.items()}
    
    results[n_trials] = (outcome_counts, probabilities) # Store frequencies and probabilities for each set.

# Print the results for each set of trials

for n_trials in trial_sets: 
    outcome_counts, probabilities= results[n_trials]
    print(f"Results for {n_trials} tosses:")
    print(f"Frequencies of outcomes: {outcome_counts}")
    print(f"Probabilities of outcomes: {probabilities}\n")

Results for 100 tosses:
Frequencies of outcomes: Counter({'TT': 28, 'HT': 27, 'TH': 23, 'HH': 22})
Probabilities of outcomes: {'TH': 0.23, 'TT': 0.28, 'HH': 0.22, 'HT': 0.27}

Results for 500 tosses:
Frequencies of outcomes: Counter({'TH': 145, 'HH': 122, 'TT': 118, 'HT': 115})
Probabilities of outcomes: {'TT': 0.236, 'TH': 0.29, 'HT': 0.23, 'HH': 0.244}

Results for 1000 tosses:
Frequencies of outcomes: Counter({'HT': 277, 'TH': 254, 'HH': 240, 'TT': 229})
Probabilities of outcomes: {'TT': 0.229, 'TH': 0.254, 'HT': 0.277, 'HH': 0.24}

# Visualize the results using bar charts for each set of trials

labels = ['HH', 'HT', 'TH', 'TT']
colors = ['green', 'red', 'blue', 'orange']

fig, axes = plt.subplots(2, len(trial_sets), figsize=(10, 5 * len(trial_sets)))

#Bar chart for frequencies

for idx, n_trials in enumerate(trial_sets):
    outcome_counts, probabilities = results[n_trials]
    axes[0, idx].bar(labels, outcome_counts.values(), color=colors)
    axes[0, idx].set_title(f"Frequencies for two coin {n_trials} tosses")
    axes[0, idx].set_xlabel("Outcome")
    axes[0, idx].set_ylabel("Count")
    
    #Bar chart for probabailities

    axes[1, idx].bar(labels, probabilities.values(), color=colors)
    axes[1, idx].set_title(f"Probabilities for two coin {n_trials} tosses")
    axes[1, idx].set_xlabel("Outcome")
    axes[1, idx].set_ylabel("Probability")


plt.tight_layout()
plt.show()


# Theoretical probabilities (since each outcome has a 1/4 chance)

theoretical_probabilities = {'HH': 1/4, 'HT': 1/4, 'TH': 1/4, 'TT': 1/4}
print("\nTheoretical Probabilities:", theoretical_probabilities)

Theoretical Probabilities: {'HH': 0.25, 'HT': 0.25, 'TH': 0.25, 'TT': 0.25}

```
![download](https://github.com/user-attachments/assets/ba0bf5f2-4654-462b-a32f-dfd9309042bb)



