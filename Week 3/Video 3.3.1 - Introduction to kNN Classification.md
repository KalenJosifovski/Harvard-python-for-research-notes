---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [machine-learning, classification, kNN]  
---

# Summary

## 1. **Extracting Features and Labels**  
   - **Syntax**:  
     ```python  
     # Example dataset with features (x1, x2) and labels (class)  
     features = [[60, 170], [55, 160], [70, 180], [65, 175]]  # [weight, height]  
     labels = ["Red", "Blue", "Red", "Blue"]  
     ```  
   - **Description**:  
     - Features are stored as numerical lists (e.g., weight and height).  
     - Labels represent categorical classes (e.g., "Red" or "Blue").  

## 2. **Basic kNN Classification**  
   - **Syntax**:  
     ```python  
     from sklearn.neighbors import KNeighborsClassifier  
     knn = KNeighborsClassifier(n_neighbors=3)  
     knn.fit(features, labels)  
     prediction = knn.predict([[62, 168]])  # Predict class for new data  
     ```  
   - **Description**:  
     - Uses `scikit-learn`’s `KNeighborsClassifier` with `n_neighbors=3`.  
     - `.fit()` trains the model; `.predict()` classifies new points.  

## 3. **Distance Calculation (Euclidean)**  
   - **Syntax**:  
     ```python  
     import numpy as np  
     def euclidean_distance(point1, point2):  
         return np.sqrt(np.sum((np.array(point1) - np.array(point2))**2))  
     ```  
   - **Example**:  
     ```python  
     distance = euclidean_distance([60, 170], [62, 168])  # ~3.6 units  
     ```  

## 4. **Manual kNN Implementation**  
   - **Syntax**:  
     ```python  
     def manual_knn(new_point, features, labels, k=3):  
         distances = []  
         for i, point in enumerate(features):  
             dist = euclidean_distance(new_point, point)  
             distances.append((dist, labels[i]))  
         distances.sort()  
         neighbors = distances[:k]  
         counts = {}  
         for neighbor in neighbors:  
             label = neighbor[1]  
             counts[label] = counts.get(label, 0) + 1  
         return max(counts, key=counts.get)  
     ```  
   - **Example**:  
     ```python  
     manual_knn([62, 168], features, labels, k=3)  # Returns "Blue"  
     ```  

## 5. **Choosing Optimal `k`**  
   - **Syntax**:  
     ```python  
     # Cross-validation to select k  
     from sklearn.model_selection import cross_val_score  
     k_values = [1, 3, 5, 7]  
     for k in k_values:  
         knn = KNeighborsClassifier(n_neighbors=k)  
         scores = cross_val_score(knn, features, labels, cv=2)  
         print(f"k={k}: Accuracy = {np.mean(scores):.2f}")  
     ```  
   - **Description**:  
     - Evaluates model accuracy for different `k` values to avoid overfitting/underfitting.  

---

### Key Takeaways:  
1. **kNN Workflow**:  
   - Calculate distances → Sort neighbors → Majority vote.  
2. **Library Use**:  
   - Prefer `scikit-learn` for optimized implementations.  
3. **Hyperparameter Tuning**:  
   - Validate `k` using cross-validation to balance bias and variance.  
4. **Distance Metrics**:  
   - Euclidean is default, but experiment with Manhattan/Cosine for non-linear data.  