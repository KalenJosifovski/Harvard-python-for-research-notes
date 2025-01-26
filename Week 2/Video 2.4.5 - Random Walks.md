---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [numpy, random-walks, visualization]  
---

# Summary

## 1. **Defining the Random Walk**  
   - **Syntax**: Position at step `k` = Initial position + cumulative sum of displacements.  
   - **Description**: A random walk starts at an origin (e.g., [0, 0]) and accumulates random steps (displacements).  
   - **Mathematical Formulation**:  
     $$ X_k = X_0 + \sum_{i=1}^k \Delta x_i $$  
     where $\Delta x_i$ are displacements sampled from a distribution (e.g., normal distribution).

## 2. **Generating Displacements**  
   - **Syntax**: `np.random.normal(mean, std_dev, size=(dimensions, steps))`  
   - **Description**: Create 2D displacement vectors (x and y components) from a normal distribution.  
   - **Example**:  
     ```python  
     import numpy as np  
     steps = 100  
     # Generate x and y displacements (2 rows, 100 columns)  
     delta_x = np.random.normal(0, 1, (2, steps))  
     ```

## 3. **Cumulative Sum for Positions**  
   - **Syntax**: `np.cumsum(array, axis=1)`  
   - **Description**: Compute cumulative positions along the steps axis.  
   - **Example**:  
     ```python  
     X = np.cumsum(delta_x, axis=1)  
     ```

## 4. **Including the Initial Position**  
   - **Syntax**: `np.concatenate((initial_position, cumulative_displacements), axis=1)`  
   - **Description**: Add the origin (0, 0) to the start of the walk.  
   - **Example**:  
     ```python  
     X0 = np.array([[0], [0]])  # Initial position (0, 0)  
     X_full = np.concatenate((X0, X), axis=1)  
     ```

## 5. **Plotting the Random Walk**  
   - **Syntax**: `plt.plot(x_coords, y_coords, style)`  
   - **Description**: Visualize the walk with markers and lines.  
   - **Example**:  
     ```python  
     import matplotlib.pyplot as plt  
     plt.plot(X_full[0], X_full[1], 'ro-', linewidth=0.5, markersize=3)  
     plt.xlabel("X Position")  
     plt.ylabel("Y Position")  
     plt.title("2D Random Walk (100 Steps)")  
     plt.savefig("random_walk.pdf")  
     plt.show()  
     ```

---

### Key Takeaways:  
1. **Vectorized Operations**:  
   - Use `np.random.normal` and `np.cumsum` for efficient displacement generation and position calculation.  
2. **Initial Position**:  
   - Always concatenate `[0, 0]` to include the starting point in plots.  
3. **Visualization**:  
   - Use `plt.plot` with `'ro-'` for red circles connected by lines.  
4. **Scalability**:  
   - Adjust `steps` (e.g., 10,000) to simulate long walks.  
5. **Applications**:  
   - Model Brownian motion, stock prices, or spatial movement patterns.  