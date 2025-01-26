---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [classification, logistic-regression, visualization]  
---

# Summary

## 1. **Grid Creation**  
   - **Syntax**:  
     ```python  
     import numpy as np  

     # Define grid ranges for X1 and X2  
     x1_grid = np.arange(-5, 5, 0.1)  # From -5 to 5 in steps of 0.1  
     x2_grid = np.arange(-5, 5, 0.1)  

     # Create meshgrid  
     xx1, xx2 = np.meshgrid(x1_grid, x2_grid)  
     ```  
   - **Output**:  
     - `xx1`, `xx2`: Matrices representing all (X1, X2) coordinate pairs.  

## 2. **Probability Computation Across Grid**  
   - **Flatten Grids**:  
     ```python  
     X1_flat = xx1.ravel()  # Convert grid matrix to 1D vector (e.g., shape: 10000,)  
     X2_flat = xx2.ravel()  
     ```  
   - **Combine Features**:  
     ```python  
     grid_points = np.column_stack((X1_flat, X2_flat))  # Shape: (n_grid_points, 2)  
     ```  
   - **Predict Probabilities**:  
     ```python  
     probs = clf.predict_proba(grid_points)  # Returns (n_grid_points, 2) matrix  
     prob_class1 = probs[:, 1]               # Extract P(Y=1 | X) for all points  
     ```  

## 3. **Reshape for Visualization**  
   - **Syntax**:  
     ```python  
     # Reshape probabilities to match grid dimensions  
     Z = prob_class1.reshape(xx1.shape)  # Shape matches xx1 (100, 100)  
     ```  

## 4. **Visualization with Contour Plots**  
   - **Syntax**:  
     ```python  
     import matplotlib.pyplot as plt  

     plt.figure(figsize=(10, 6))  
     contour = plt.contourf(xx1, xx2, Z, alpha=0.8, cmap="viridis")  
     plt.colorbar(contour, label="Probability of Class 1")  
     plt.scatter(X_train[:, 0], X_train[:, 1], c=y_train, edgecolor="k", cmap="coolwarm")  
     plt.xlabel("$X_1$")  
     plt.ylabel("$X_2$")  
     plt.title("Class 1 Probability Heatmap")  
     plt.show()  
     ```  
   - **Output**:  
     - Heatmap showing decision boundary (where P(Y=1 | X) = 0.5).  
     - Training data overlaid to validate alignment with predicted probabilities.  

---

### Key Takeaways:  
1. **Grid Preparation**:  
   - `np.meshgrid` creates a coordinate grid for evaluating probabilities across the feature space.  
2. **Input Formatting**:  
   - Use `ravel()` and `column_stack()` to convert grid matrices into scikit-learn compatible input.  
3. **Probability Reshaping**:  
   - Results from `predict_proba` must be reshaped to match grid dimensions for plotting.  
4. **Decision Boundary**:  
   - The 0.5 probability contour (midpoint of colorbar) represents the classifier’s decision boundary.  
5. **Visual Insights**:  
   - Heatmaps reveal how predictor variables influence class probabilities (e.g., linear vs. non-linear boundaries).  
6. **Code Reproducibility**:  
   - Adjust grid ranges (`np.arange`) and step sizes to control plot resolution.  