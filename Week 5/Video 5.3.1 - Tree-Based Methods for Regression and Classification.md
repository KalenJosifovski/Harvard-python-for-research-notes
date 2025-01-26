---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [tree-methods, regression, classification, random-forest]  
---

# Summary

## 1. **Decision Trees: Core Concept**  
   - **Goal**: Partition predictor space into homogeneous regions using axis-aligned splits.  
   - **Prediction**:  
     - **Regression**: Mean of training outcomes in the region.  
     - **Classification**: Mode (most frequent class) in the region.  

## 2. **Splitting Criteria**  
   - **Regression**: Minimize **Residual Sum of Squares (RSS)**:  
     \[ \text{RSS} = \sum (y_i - \hat{y}_i)^2 \]  
   - **Classification**: Minimize impurity via **Gini Index** or **Cross-Entropy**:  
     - **Gini Index**:  
       \[ G = \sum_{k=1}^K \hat{p}_{mk}(1 - \hat{p}_{mk}) \]  
     - **Cross-Entropy**:  
       \[ D = -\sum_{k=1}^K \hat{p}_{mk} \log \hat{p}_{mk} \]  
     - \( \hat{p}_{mk} \): Proportion of class \( k \) in region \( m \).  

## 3. **Tree Structure**  
   - **Nodes**: Represent splitting rules (e.g., \( X_1 \leq 5 \)).  
   - **Leaves**: Terminal nodes providing final predictions.  
   - **Recursive Process**: Split regions until stopping criteria (e.g., max depth, minimum samples per leaf).  

## 4. **Random Forests**  
   - **Ensemble Method**: Combine predictions from multiple decorrelated decision trees.  
   - **Randomness Introduced By**:  
     - **Bootstrapping**: Train each tree on a random subset of data.  
     - **Feature Randomness**: Split nodes using random subsets of predictors.  
   - **Aggregation**:  
     - **Regression**: Average predictions.  
     - **Classification**: Majority vote.  

## 5. **Implementation Example (scikit-learn)**  
   - **Decision Tree (Regression)**:  
     ```python  
     from sklearn.tree import DecisionTreeRegressor  

     # Fit model  
     tree_reg = DecisionTreeRegressor(max_depth=3)  
     tree_reg.fit(X_train, y_train)  
     ```  
   - **Random Forest (Classification)**:  
     ```python  
     from sklearn.ensemble import RandomForestClassifier  

     # Fit model  
     rf_clf = RandomForestClassifier(n_estimators=100, max_features="sqrt")  
     rf_clf.fit(X_train, y_train)  
     ```  

---

### Key Takeaways:  
1. **Interpretability vs. Flexibility**:  
   - Decision trees are intuitive but prone to overfitting.  
   - Random forests mitigate overfitting through ensemble averaging.  
2. **Hyperparameters**:  
   - **Tree Depth**: Controls model complexity (shallow = underfit, deep = overfit).  
   - **Number of Trees**: More trees reduce variance but increase computational cost.  
3. **Axis-Aligned Splits**:  
   - Decision boundaries are orthogonal, limiting flexibility for diagonal relationships.  
4. **Practical Use**:  
   - Use random forests for robust performance; tune `max_depth`, `n_estimators`, and `max_features`.  
5. **Model Diagnostics**:  
   - Evaluate regression with MSE/RMSE; classification with accuracy, ROC-AUC, or confusion matrices.  