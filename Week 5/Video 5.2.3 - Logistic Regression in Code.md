---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [classification, logistic-regression, scikit-learn]  
---

# Summary

## 1. **Data Preparation**  
   - **Combine Features**:  
     ```python  
     import numpy as np  

     # Stack features for Class 1 (x1, y1) and Class 2 (x2, y2)  
     X_class1 = np.column_stack((x1, y1))  # Shape: (n, 2)  
     X_class2 = np.column_stack((x2, y2))  
     X = np.vstack((X_class1, X_class2))    # Combine into (2n, 2) matrix  
     ```  
   - **Create Target Vector**:  
     ```python  
     y = np.hstack((np.ones(n), np.zeros(n)))  # Class 1: 1s, Class 2: 0s  
     ```  

## 2. **Train-Test Split**  
   - **Syntax**:  
     ```python  
     from sklearn.model_selection import train_test_split  

     X_train, X_test, y_train, y_test = train_test_split(  
         X, y, test_size=0.5, random_state=42  
     )  
     ```  
   - **Purpose**:  
     - Split data into 50% training and 50% testing sets.  

## 3. **Model Training**  
   - **Syntax**:  
     ```python  
     from sklearn.linear_model import LogisticRegression  

     clf = LogisticRegression()  
     clf.fit(X_train, y_train)  
     ```  
   - **Output**:  
     - Trained classifier with coefficients (`clf.coef_`) and intercept (`clf.intercept_`).  

## 4. **Model Evaluation**  
   - **Accuracy Score**:  
     ```python  
     accuracy = clf.score(X_test, y_test)  # Example: 0.88 (88% accuracy)  
     ```  
   - **Probability Prediction**:  
     ```python  
     # Reshape input for single sample prediction  
     sample = np.array([[-2, 0]]).reshape(1, -1)  
     prob_class1 = clf.predict_proba(sample)[0][1]  # P(Y=1 | X) ≈ 0.97  
     ```  
   - **Class Prediction**:  
     ```python  
     predicted_class = clf.predict(sample)  # Returns 1 (Class 1)  
     ```  

---

### Key Takeaways:  
1. **Data Structuring**:  
   - Combine features into a matrix (`X`) and labels into a vector (`y`) for scikit-learn compatibility.  
2. **Input Reshaping**:  
   - Use `.reshape(1, -1)` for single-sample predictions to avoid dimension errors.  
3. **Probability Output**:  
   - `predict_proba()` returns probabilities for both classes (sum to 1).  
4. **Class Assignment**:  
   - The class with probability > 0.5 is predicted (default threshold).  
5. **Practical Workflow**:  
   - Prepare data → Split → Train → Evaluate → Predict.  
6. **Reproducibility**:  
   - Use `random_state` in `train_test_split` for consistent results.  