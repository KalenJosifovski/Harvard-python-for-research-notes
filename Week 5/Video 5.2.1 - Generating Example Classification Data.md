---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [classification, synthetic-data, matplotlib, scipy]  
---

# Summary

## 1. **Generating Synthetic Classification Data**  
   - **Function Definition**:  
     ```python  
     import numpy as np  
     import scipy.stats as ss  
     import matplotlib.pyplot as plt  

     def gen_data(n, h, sd1, sd2):  
         # Class 1: Centered at (-h, 0) with standard deviation sd1  
         x1 = ss.norm.rvs(loc=-h, scale=sd1, size=n)  
         y1 = ss.norm.rvs(loc=0, scale=sd1, size=n)  

         # Class 2: Centered at (h, 0) with standard deviation sd2  
         x2 = ss.norm.rvs(loc=h, scale=sd2, size=n)  
         y2 = ss.norm.rvs(loc=0, scale=sd2, size=n)  

         return x1, y1, x2, y2  
     ```  
   - **Parameters**:  
     - `n`: Number of samples per class.  
     - `h`: Distance from the origin for class centers.  
     - `sd1`, `sd2`: Standard deviations for class 1 and 2.  

## 2. **Example Data Generation**  
   - **Syntax**:  
     ```python  
     # Generate 1000 samples per class  
     x1, y1, x2, y2 = gen_data(n=1000, h=1.5, sd1=1, sd2=1.5)  
     ```  
   - **Output**:  
     - Class 1: Centered at `(-1.5, 0)` with tighter spread (`sd1=1`).  
     - Class 2: Centered at `(1.5, 0)` with broader spread (`sd2=1.5`).  

## 3. **Visualization**  
   - **Plotting Function**:  
     ```python  
     def plot_data(x1, y1, x2, y2):  
         plt.figure(figsize=(8, 6))  
         plt.scatter(x1, y1, s=2, label="Class 1", color="blue")  
         plt.scatter(x2, y2, s=2, label="Class 2", color="orange")  
         plt.xlabel("$X_1$")  # LaTeX formatting for subscript  
         plt.ylabel("$X_2$")  
         plt.legend()  
         plt.grid(True)  
         plt.show()  
     ```  
   - **Usage**:  
     ```python  
     plot_data(x1, y1, x2, y2)  
     ```  
   - **Plot Output**:  
     - Two clusters: Blue (left) and orange (right).  
     - Class 2 (orange) has a wider spread due to higher `sd2`.  

---

### Key Takeaways:  
1. **Class Separation**:  
   - Distance `h` controls separation between class centers.  
   - Larger `h` improves distinguishability.  
2. **Spread Control**:  
   - `sd1` and `sd2` determine cluster tightness.  
   - Higher values increase overlap between classes.  
3. **Reproducibility**:  
   - Add `np.random.seed()` in `gen_data` for consistent results.  
4. **Visual Clarity**:  
   - Use legends and LaTeX labels for professional-quality plots.  
5. **Use Case**:  
   - Ideal for testing classification algorithms (e.g., logistic regression, SVM).  