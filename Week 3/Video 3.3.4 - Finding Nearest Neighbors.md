---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [machine-learning, kNN, numpy]  
---

# Summary

## 1. **Creating a Test Dataset**  
   - **Syntax**:  
     ```python  
     import numpy as np  
     points = np.array([[1,1], [1,2], [1,3], [2,1], [2,2], [2,3], [3,1], [3,2], [3,3]])  
     p = np.array([2.5, 2])  # Point to classify  
     ```  
   - **Description**:  
     - Defines a 3x3 grid of points and a target point `p` for classification.  

## 2. **Calculating Distances**  
   - **Syntax**:  
     ```python  
     distances = np.zeros(len(points))  
     for i in range(len(points)):  
         distances[i] = np.sqrt(np.sum((p - points[i])**2))  
     ```  
   - **Example Output**:  
     ```python  
     print(distances)  # [1.802, 1.5, 1.802, 1.118, 0.5, 1.118, 2.062, 1.118, 2.062]  
     ```  

## 3. **Sorting Distances with `argsort`**  
   - **Syntax**:  
     ```python  
     ind = np.argsort(distances)  
     k_nearest_indices = ind[:k]  # Indices of k-nearest neighbors  
     ```  
   - **Example**:  
     ```python  
     k = 2  
     print(points[k_nearest_indices])  # [[2 2], [3 2]]  
     ```  

## 4. **Finding Nearest Neighbors Function**  
   - **Syntax**:  
     ```python  
     def find_nearest_neighbors(p, points, k=5):  
         """  
         Returns indices of k-nearest neighbors to point p.  
         Args:  
             p (np.array): Target point.  
             points (np.array): Training data points.  
             k (int): Number of neighbors.  
         Returns:  
             np.array: Indices of nearest neighbors.  
         """  
         distances = np.sqrt(np.sum((p - points)**2, axis=1))  
         return np.argsort(distances)[:k]  
     ```  
   - **Usage**:  
     ```python  
     neighbors = find_nearest_neighbors(p, points, k=2)  
     print(neighbors)  # [4, 7] (indices of [2,2] and [3,2])  
     ```  

## 5. **Predicting Class with Majority Vote**  
   - **Syntax**:  
     ```python  
     def knn_predict(p, points, outcomes, k=5):  
         """  
         Predicts class of point p using kNN.  
         Args:  
             p (np.array): Target point.  
             points (np.array): Training data.  
             outcomes (np.array): Class labels.  
             k (int): Number of neighbors.  
         Returns:  
             int: Predicted class (0 or 1).  
         """  
         neighbors = find_nearest_neighbors(p, points, k)  
         return majority_vote(outcomes[neighbors])  # Uses previous majority_vote function  
     ```  
   - **Example**:  
     ```python  
     outcomes = np.array([0,0,0,0,1,1,1,1,1])  
     print(knn_predict(np.array([2.5, 2.7]), points, outcomes, k=2))  # Output: 1  
     ```  

---

### Key Takeaways:  
1. **Distance Calculation**:  
   - Use vectorized NumPy operations for efficient Euclidean distance computation.  
2. **Neighbor Identification**:  
   - `np.argsort()` simplifies sorting by indices to retrieve nearest neighbors.  
3. **Integration with Majority Vote**:  
   - Combine neighbor indices with class labels to predict using majority voting.  
4. **Scalability**:  
   - Works for any dimensionality (2D, 3D, etc.) by adjusting the distance formula.  