---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [regression, least-squares, numpy, grid-search]  
---

# Summary

## 1. **Grid Search for Least Squares Estimation**  
   - **Goal**: Estimate slope (\( \beta_1 \)) by minimizing the Residual Sum of Squares (RSS).  
   - **Assumption**: True intercept (\( \beta_0 \)) is known (simplified example).  

## 2. **Implementation Steps**  
   - **Define Grid of Slopes**:  
     ```python  
     import numpy as np  
     slopes = np.arange(-10, 15, 0.01)  # Test slopes from -10 to 15 in steps of 0.01  
     ```  
   - **Compute RSS for Each Slope**:  
     ```python  
     rss = []  
     beta0_true = 5  # Known intercept  
     for slope in slopes:  
         residuals = y - (beta0_true + slope * x)  # Calculate residuals  
         rss.append(np.sum(residuals**2))           # Sum of squared residuals  
     ```  
   - **Find Optimal Slope**:  
     ```python  
     ind_min = np.argmin(rss)            # Index of minimum RSS  
     beta1_hat = slopes[ind_min]         # Estimated slope (e.g., 2.0)  
     ```  

## 3. **Visualization**  
   - **Plot RSS vs. Slopes**:  
     ```python  
     import matplotlib.pyplot as plt  
     plt.figure()  
     plt.plot(slopes, rss, label="RSS")  
     plt.xlabel("Slope (β₁)")  
     plt.ylabel("Residual Sum of Squares")  
     plt.scatter(beta1_hat, rss[ind_min], color="red", label="Minimum RSS")  
     plt.legend()  
     plt.show()  
     ```  
   - **Output**:  
     - Convex curve with minimum at \( \hat{\beta}_1 = 2.0 \) (matches true slope in synthetic data).  

---

### Key Takeaways:  
1. **Grid Search Method**:  
   - Brute-force approach to find the slope minimizing RSS.  
   - Useful for pedagogical purposes but inefficient for high-dimensional problems.  
2. **Synthetic Data Validation**:  
   - With known \( \beta_0 \), the estimated \( \hat{\beta}_1 \) matches the true value (2.0), confirming method accuracy.  
3. **RSS Visualization**:  
   - Plotting RSS against slopes demonstrates the convexity of the loss function in linear regression.  
4. **Practical Limitations**:  
   - Closed-form solutions (e.g., \( \hat{\beta} = (X^TX)^{-1}X^Ty \)) or gradient descent are preferred for real-world efficiency.  
5. **Code Reproducibility**:  
   - Use fixed parameters (e.g., `np.random.seed()`) to ensure consistent results in synthetic examples.  