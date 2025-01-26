---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [kNN, data-visualization, matplotlib]  
---

# Summary

## 1. **Generating Synthetic Data**  
   - **Syntax**:  
     ```python  
     from synthetic_data import generate_synthetic_data  
     predictors, outcomes = generate_synthetic_data(n=50)  
     ```  
   - **Description**:  
     - Uses `generate_synthetic_data` to create 50 points per class from bivariate normal distributions.  
     - `predictors`: 2D array of (x, y) coordinates.  
     - `outcomes`: 1D array of class labels (0 or 1).  

## 2. **Creating Prediction Grid**  
   - **Syntax**:  
     ```python  
     limits = (-3, 4, -3, 4)  # (x_min, x_max, y_min, y_max)  
     h = 0.1  # Step size  
     xx, yy, grid = make_prediction_grid(predictors, outcomes, limits, h, k=5)  
     ```  
   - **Description**:  
     - `make_prediction_grid` generates a grid of points and predicts classes using kNN.  
     - Returns coordinate matrices (`xx`, `yy`) and class predictions (`grid`).  

## 3. **Visualizing Decision Boundaries**  
   - **Syntax**:  
     ```python  
     def plot_prediction_grid(xx, yy, grid, filename):  
         plt.pcolormesh(xx, yy, grid, cmap="coolwarm", alpha=0.1)  
         plt.scatter(predictors[:,0], predictors[:,1], c=outcomes, cmap="coolwarm")  
         plt.savefig(filename)  
         plt.close()  
     ```  
   - **Example**:  
     ```python  
     plot_prediction_grid(xx, yy, grid, "knn_synth_5.pdf")  
     ```  
   - **Output**:  
     - Heatmap showing predicted classes (grid) overlaid with training data points.  

## 4. **Effect of `k` on Decision Boundaries**  
   - **Case 1 (k=5)**:  
     ```python  
     _, _, grid = make_prediction_grid(..., k=5)  
     plot_prediction_grid(..., "knn_synth_5.pdf")  
     ```  
     - **Result**: Complex, non-linear decision boundaries (higher variance).  
   - **Case 2 (k=50)**:  
     ```python  
     _, _, grid = make_prediction_grid(..., k=50)  
     plot_prediction_grid(..., "knn_synth_50.pdf")  
     ```  
     - **Result**: Smoother decision boundaries (higher bias).  

---

### Key Takeaways:  
1. **Grid Construction**:  
   - `np.meshgrid` creates coordinate matrices for evaluating kNN across a region.  
2. **k Value Impact**:  
   - Small `k` (e.g., 5) captures local patterns but risks overfitting.  
   - Large `k` (e.g., 50) smooths boundaries but may under-fit.  
3. **Bias-Variance Tradeoff**:  
   - Choose intermediate `k` values to balance model flexibility and generalisation.  
4. **Visual Validation**:  
   - Use `pcolormesh` for grid predictions and `scatter` for training data overlay.  