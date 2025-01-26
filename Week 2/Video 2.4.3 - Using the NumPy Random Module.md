---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [numpy, random-module, vectorization]  
---

# Summary

## 1. **Uniform Distribution (`np.random.random`)**  
   - **Syntax**:  
     - Single value: `np.random.random()`  
     - Array: `np.random.random(size=(rows, cols))`  
   - **Description**: Generates floats uniformly distributed between 0 (inclusive) and 1 (exclusive).  
   - **Examples**:  
     ```python  
     import numpy as np  
     # Single value  
     rand_float = np.random.random()  
     # 1D array of 5 values  
     arr_1d = np.random.random(5)  
     # 2D array (5x3)  
     arr_2d = np.random.random((5, 3))  
     ```

## 2. **Normal Distribution (`np.random.normal`)**  
   - **Syntax**: `np.random.normal(mean, std_dev, size)`  
   - **Description**: Generates values from a normal distribution with specified mean and standard deviation.  
   - **Examples**:  
     ```python  
     # Standard normal (mean=0, std=1)  
     std_normal = np.random.normal(0, 1, 1000)  
     # Custom normal (mean=5, std=2)  
     custom_normal = np.random.normal(5, 2, (10, 3))  # 10x3 array  
     ```

## 3. **Random Integers (`np.random.randint`)**  
   - **Syntax**: `np.random.randint(low, high, size)`  
   - **Description**: Generates integers between `low` (inclusive) and `high` (exclusive).  
   - **Examples**:  
     ```python  
     # Single die roll (1-6)  
     die_roll = np.random.randint(1, 7)  
     # 2D array of 100 trials x 10 dice  
     dice_rolls = np.random.randint(1, 7, (100, 10))  
     ```

## 4. **Summing Across Axes (`np.sum`)**  
   - **Syntax**: `np.sum(array, axis=0/1)`  
   - **Description**:  
     - `axis=0`: Sum columns (row-wise).  
     - `axis=1`: Sum rows (column-wise).  
   - **Example**:  
     ```python  
     # Sum 10 dice rolls across columns (axis=1)  
     y = np.sum(dice_rolls, axis=1)  
     ```

## 5. **Central Limit Theorem (CLT) Example**  
   - **Syntax**: Combine `np.random.randint` and `np.sum` for vectorized simulations.  
   - **Description**: Summing 10 dice rolls (1M trials) produces a normal distribution.  
   - **Example**:  
     ```python  
     # Simulate 1M trials of 10 dice rolls  
     dice_rolls = np.random.randint(1, 7, (1_000_000, 10))  
     y = np.sum(dice_rolls, axis=1)  
     # Plot histogram  
     import matplotlib.pyplot as plt  
     plt.hist(y, bins=50, density=True)  
     plt.show()  
     ```

---

### Key Takeaways:  
1. **NumPy Efficiency**:  
   - Vectorized operations (e.g., `np.random.randint`) are **10x faster** than Python loops.  
2. **Distribution Functions**:  
   - Use `np.random.random` for uniform, `np.random.normal` for Gaussian, and `np.random.randint` for integer sampling.  
3. **Axis Summation**:  
   - `axis=1` sums rows to compute aggregated outcomes (e.g., sum of 10 dice per trial).  
4. **CLT in Action**:  
   - Large-scale simulations (1M+ trials) validate theoretical distributions (e.g., normal distribution from summed dice).  
5. **Best Practices**:  
   - Start with small arrays for debugging, then scale up.  
   - Use `size` parameter to generate multi-dimensional arrays directly.  