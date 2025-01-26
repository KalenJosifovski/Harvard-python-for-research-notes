---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [matplotlib, histograms, subplots]  
---

# Summary

## 1. **Basic Histogram with `plt.hist`**  
   - **Syntax**: `plt.hist(data, bins=10)`  
   - **Description**: Generates a histogram with default bins (10 bins).  
   - **Example**:  
     ```python  
     import numpy as np  
     import matplotlib.pyplot as plt  

     # Generate 1,000 samples from a standard normal distribution  
     x = np.random.normal(0, 1, 1000)  
     plt.hist(x, bins=10)  
     plt.show()  
     ```

## 2. **Customizing Bins and Normalization**  
   - **Syntax**:  
     - `bins`: Specify bin edges (e.g., `np.linspace(-5, 5, 21)` creates 20 bins).  
     - `density=True`: Normalizes the histogram to display probabilities (replaces deprecated `normed`).  
   - **Example**:  
     ```python  
     bins = np.linspace(-5, 5, 21)  # 20 bins between -5 and 5  
     plt.hist(x, bins=bins, density=True)  
     plt.show()  
     ```

## 3. **Cumulative and Step Histograms**  
   - **Syntax**:  
     - `cumulative=True`: Displays cumulative counts/probabilities.  
     - `histtype='step'`: Draws a step-style histogram.  
   - **Example**:  
     ```python  
     plt.hist(x, bins=30, density=True, cumulative=True, histtype='step')  
     plt.show()  
     ```

## 4. **Gamma Distribution Example**  
   - **Syntax**: `np.random.gamma(shape, scale, size)`  
   - **Description**: Generates samples from a gamma distribution.  
   - **Example**:  
     ```python  
     gamma_data = np.random.gamma(2, 3, 100000)  # Shape=2, Scale=3, 100k samples  
     plt.hist(gamma_data, bins=50, density=True)  
     plt.show()  
     ```

## 5. **Subplots for Multiple Histograms**  
   - **Syntax**: `plt.subplot(rows, cols, plot_number)`  
   - **Description**: Arranges multiple plots in a grid.  
   - **Example**:  
     ```python  
     plt.figure(figsize=(10, 8))  

     # Subplot 1: Default histogram  
     plt.subplot(2, 2, 1)  
     plt.hist(gamma_data, bins=30)  

     # Subplot 2: Normalized histogram  
     plt.subplot(2, 2, 2)  
     plt.hist(gamma_data, bins=30, density=True)  

     # Subplot 3: Cumulative histogram  
     plt.subplot(2, 2, 3)  
     plt.hist(gamma_data, bins=30, cumulative=True)  

     # Subplot 4: Step histogram  
     plt.subplot(2, 2, 4)  
     plt.hist(gamma_data, bins=30, histtype='step')  

     plt.tight_layout()  
     plt.show()  
     ```

---

### Key Takeaways:  
1. **Bin Specification**:  
   - Use `np.linspace(start, end, num_points)` to define bin edges.  
   - `num_points = N + 1` creates `N` bins (e.g., 21 points → 20 bins).  
2. **Normalization**:  
   - Use `density=True` (not `normed`) for probability density histograms.  
3. **Advanced Options**:  
   - Combine `cumulative` and `histtype` for specialized visualizations.  
4. **Subplots**:  
   - Use `plt.subplot()` to organize multiple plots in a single figure.  
   - Call `plt.tight_layout()` to prevent overlapping subplots.  
5. **Gamma Distribution**:  
   - Large sample sizes (e.g., 100,000) produce smoother histograms.  