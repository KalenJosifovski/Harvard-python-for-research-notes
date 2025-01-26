---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [random-forest, ensemble-methods, scikit-learn]  
---

# Summary

## 1. **Random Forest Prediction Mechanism**  
   - **Regression**: Final prediction = Average of predictions from all trees.  
   - **Classification**: Final prediction = Majority vote (mode) of predictions from all trees.  

## 2. **Sources of Randomness**  
   - **Bootstrap Aggregation (Bagging)**:  
     - Each tree is trained on a bootstrap sample (random subset of data **with replacement**).  
     - Example: Original dataset with 1,000 observations → Each bootstrap sample has ~1,000 observations (some duplicates).  
   - **Feature Randomness**:  
     - For **each split** in a tree, a random subset of predictors is considered (e.g., 3 out of 9 features).  
     - Controlled by `max_features` in scikit-learn.  

## 3. **Key Benefits**  
   - **Decorrelated Trees**: Reduces overfitting by ensuring trees are diverse.  
   - **Out-of-Bag (OOB) Evaluation**:  
     - Unseen data in bootstrap samples (~37% of observations) can estimate model performance.  

## 4. **Implementation Example (scikit-learn)**  
   - **Regression**:  
     ```python  
     from sklearn.ensemble import RandomForestRegressor  

     # Fit model with 100 trees, 3 features per split  
     rf_reg = RandomForestRegressor(n_estimators=100, max_features=3, bootstrap=True)  
     rf_reg.fit(X_train, y_train)  
     ```  
   - **Classification**:  
     ```python  
     from sklearn.ensemble import RandomForestClassifier  

     # Fit model with 50 trees, sqrt(features) per split  
     rf_clf = RandomForestClassifier(n_estimators=50, max_features="sqrt", bootstrap=True)  
     rf_clf.fit(X_train, y_train)  
     ```  

## 5. **Hyperparameters**  
   - `n_estimators`: Number of trees (higher → better performance but slower).  
   - `max_features`: Features considered per split (√p for classification, p/3 for regression).  
   - `bootstrap`: Whether to use bootstrap sampling (default: `True`).  

---

### Key Takeaways:  
1. **Ensemble Power**:  
   - Random forests combine predictions from **decorrelated decision trees** to reduce variance and overfitting.  
2. **Feature Subsetting**:  
   - `max_features` controls diversity; smaller values increase randomness but may improve robustness.  
3. **Practical Tips**:  
   - Use OOB scores (`oob_score=True`) for quick validation.  
   - Tune `n_estimators` and `max_features` for optimal performance.  
4. **Scikit-learn Workflow**:  
   - Define model → Fit → Predict (similar API to other sklearn estimators).  