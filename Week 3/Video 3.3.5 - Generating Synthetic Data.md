---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [synthetic-data, numpy, data-generation]  
---

# Summary

## 1. **Generating Bivariate Normal Data**  
   - **Syntax**:  
     ```python  
     import numpy as np  
     # Class 0: Mean = [0, 0], Covariance = identity matrix  
     class0 = np.random.multivariate_normal(mean=[0, 0], cov=np.eye(2), size=n)  
     # Class 1: Mean = [1, 1], Covariance = identity matrix  
     class1 = np.random.multivariate_normal(mean=[1, 1], cov=np.eye(2), size=n)  
     ```  
   - **Description**:  
     - Uses `np.random.multivariate_normal` to generate synthetic data for two classes.  
     - Class 0 centered at `(0, 0)`, Class 1 centered at `(1, 1)`.  

## 2. **Combining Data and Labels**  
   - **Syntax**:  
     ```python  
     # Concatenate points  
     points = np.concatenate((class0, class1), axis=0)  
     # Generate outcomes (0 for class0, 1 for class1)  
     outcomes = np.concatenate((np.repeat(0, n), np.repeat(1, n)))  
     ```  
   - **Example**:  
     ```python  
     n = 20  
     points, outcomes = generate_synthetic_data(n)  
     print(points.shape)  # (40, 2)  
     print(outcomes[:5])   # [0 0 0 0 0]  
     ```  

## 3. **Reusable Data Generation Function**  
   - **Syntax**:  
     ```python  
     def generate_synthetic_data(n=50):  
         """  
         Generates synthetic 2D data with two classes.  
         Args:  
             n (int): Number of samples per class.  
         Returns:  
             tuple: (points, outcomes)  
         """  
         class0 = np.random.multivariate_normal([0, 0], np.eye(2), n)  
         class1 = np.random.multivariate_normal([1, 1], np.eye(2), n)  
         points = np.concatenate((class0, class1), axis=0)  
         outcomes = np.concatenate((np.repeat(0, n), np.repeat(1, n)))  
         return (points, outcomes)  
     ```  
   - **Usage**:  
     ```python  
     points, outcomes = generate_synthetic_data(n=20)  
     ```  

## 4. **Visualizing Synthetic Data**  
   - **Syntax**:  
     ```python  
     import matplotlib.pyplot as plt  
     # Plot Class 0 (Red)  
     plt.scatter(points[:n, 0], points[:n, 1], color='red', label='Class 0')  
     # Plot Class 1 (Blue)  
     plt.scatter(points[n:, 0], points[n:, 1], color='blue', label='Class 1')  
     plt.legend()  
     plt.savefig('bivariate_data.pdf')  
     plt.show()  
     ```  
   - **Output**:  
     - A scatter plot with two clusters: red (class 0) and blue (class 1).  

---

### Key Takeaways:  
1. **Synthetic Data Purpose**:  
   - Useful for testing algorithms where ground truth is known.  
2. **Bivariate Distributions**:  
   - Use `np.random.multivariate_normal` to simulate 2D data clusters.  
3. **Label Alignment**:  
   - Ensure outcomes array matches the order of concatenated data points.  
4. **Visual Validation**:  
   - Plotting confirms data separation and distribution correctness.  