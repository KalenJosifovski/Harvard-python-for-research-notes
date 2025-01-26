---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [kNN, scikit-learn, classification]  
---

# Summary

## 1. **Loading the Iris Dataset**  
   - **Syntax**:  
     ```python  
     from sklearn import datasets  
     iris = datasets.load_iris()  
     predictors = iris.data[:, :2]  # Use first two features (sepal length/width)  
     outcomes = iris.target          # Class labels (0, 1, 2 for Iris species)  
     ```  
   - **Description**:  
     - The Iris dataset contains 150 observations with 4 features; only sepal length/width are used here.  

## 2. **Visualizing Iris Data**  
   - **Syntax**:  
     ```python  
     import matplotlib.pyplot as plt  
     # Plot class 0 (red)  
     plt.scatter(predictors[outcomes == 0][:, 0], predictors[outcomes == 0][:, 1], color='red', label='Setosa')  
     # Plot class 1 (green)  
     plt.scatter(predictors[outcomes == 1][:, 0], predictors[outcomes == 1][:, 1], color='green', label='Versicolor')  
     # Plot class 2 (blue)  
     plt.scatter(predictors[outcomes == 2][:, 0], predictors[outcomes == 2][:, 1], color='blue', label='Virginica')  
     plt.legend()  
     plt.savefig("iris.pdf")  
     ```  
   - **Output**:  
     - A scatter plot showing three Iris species clusters based on sepal measurements.  

## 3. **Homemade kNN Predictions**  
   - **Syntax**:  
     ```python  
     # Use previously defined knn_predict function  
     my_predictions = np.array([knn_predict(p, predictors, outcomes, k=5) for p in predictors])  
     ```  
   - **Description**:  
     - Predicts labels for all training points using a custom kNN implementation.  

## 4. **SciKit-Learn kNN Implementation**  
   - **Syntax**:  
     ```python  
     from sklearn.neighbors import KNeighborsClassifier  
     knn = KNeighborsClassifier(n_neighbors=5)  
     knn.fit(predictors, outcomes)  
     sk_predictions = knn.predict(predictors)  
     ```  
   - **Description**:  
     - Trains and predicts using SciKit-Learn’s optimized kNN classifier.  

## 5. **Model Comparison**  
   - **Agreement Between Models**:  
     ```python  
     agreement = np.mean(sk_predictions == my_predictions) * 100  
     print(f"Agreement: {agreement:.1f}%")  # ~96%  
     ```  
   - **Accuracy vs. True Labels**:  
     ```python  
     sk_accuracy = np.mean(sk_predictions == outcomes) * 100  # ~83%  
     my_accuracy = np.mean(my_predictions == outcomes) * 100   # ~85%  
     ```  
   - **Insight**:  
     - The homemade classifier slightly outperforms SciKit-Learn on training data (due to implementation nuances).  

---

### Key Takeaways:  
1. **Feature Selection**:  
   - Using fewer features (sepal length/width) simplifies visualization but may reduce accuracy.  
2. **Decision Boundaries**:  
   - Prediction grid plots reveal how kNN classifies regions of the feature space.  
3. **Library vs. Custom Code**:  
   - SciKit-Learn provides optimized, scalable implementations, while custom code offers flexibility.  
4. **Overfitting Risk**:  
   - High training accuracy (e.g., 85%) may indicate overfitting if test accuracy is lower.  