---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-random, simulations, central-limit-theorem]  
---

# Summary

## 1. **Single Die Roll Simulation**  
   - **Syntax**: Use `random.choice()` with `range(1, 7)` in a loop.  
   - **Description**: Simulate rolling a die multiple times and visualize frequency with a histogram.  
   - **Example**:  
     ```python  
     import random  
     import matplotlib.pyplot as plt  
     import numpy as np  

     # Roll a die 100 times  
     rolls = [random.choice(range(1, 7)) for _ in range(100)]  
     # Plot histogram with 6 bins (aligned to die faces)  
     bins = np.linspace(0.5, 6.5, 7)  # Bins centered at 1-6  
     plt.hist(rolls, bins=bins, edgecolor='black')  
     plt.title("Single Die Roll (100 trials)")  
     plt.show()  
     ```

## 2. **Law of Large Numbers**  
   - **Syntax**: Increase sample size (e.g., 10,000 or 1,000,000 trials).  
   - **Description**: Larger samples produce flatter histograms, confirming uniform probability.  
   - **Example**:  
     ```python  
     rolls_large = [random.choice(range(1, 7)) for _ in range(10_000)]  
     plt.hist(rolls_large, bins=bins, density=True)  # Normalized  
     plt.title("Single Die Roll (10,000 trials)")  
     plt.show()  
     ```

## 3. **Sum of 10 Dice (Central Limit Theorem)**  
   - **Syntax**: Nested loops to sum 10 dice rolls over multiple trials.  
   - **Description**: The sum of independent random variables approximates a normal distribution.  
   - **Example**:  
     ```python  
     ys = []  
     for _ in range(10_000):  
         total = sum(random.choice(range(1, 7)) for _ in range(10))  
         ys.append(total)  
     plt.hist(ys, bins=30, density=True, edgecolor='black')  
     plt.title("Sum of 10 Dice Rolls (CLT Example)")  
     plt.show()  
     ```

## 4. **Customizing Histograms**  
   - **Syntax**: Adjust bins and use `density=True` for probability density.  
   - **Example**:  
     ```python  
     plt.hist(ys, bins=np.arange(10, 61, 2), density=True, alpha=0.7)  
     plt.xlabel("Sum of 10 Dice")  
     plt.ylabel("Probability")  
     plt.show()  
     ```

---

### Key Takeaways:  
1. **Law of Large Numbers**:  
   - Larger sample sizes yield histograms closer to theoretical probabilities (flat for a fair die).  
2. **Central Limit Theorem (CLT)**:  
   - Sums of independent random variables (e.g., 10 dice) approximate a normal distribution, even if individual variables are non-normal.  
3. **Efficient Simulations**:  
   - Use list comprehensions (e.g., `[random.choice(...) for _ in range(N)]`) for large-scale simulations.  
4. **Visualization Tips**:  
   - Align histogram bins to integer outcomes (e.g., `np.linspace(0.5, 6.5, 7)` for die rolls).  
   - Use `density=True` to compare probability distributions across different sample sizes.  
5. **Practical Applications**:  
   - Simulate probabilistic systems (e.g., games, risk modeling) and validate results with statistical theory.  