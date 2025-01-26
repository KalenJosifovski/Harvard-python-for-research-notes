---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [model-evaluation, mse, overfitting, train-test-split]  
---

# Summary

## 1. **Evaluating Regression Models**  
   - **Mean Squared Error (MSE)**:  
     \[ \text{MSE} = \frac{1}{n} \sum_{i=1}^n (y_i - \hat{y}_i)^2 \]  
     - **Training MSE**: Computed on training data (used to fit the model).  
     - **Test MSE**: Computed on unseen test data (measures generalization).  

## 2. **Train-Test Split**  
   - **Syntax (scikit-learn)**:  
     ```python  
     from sklearn.model_selection import train_test_split  

     # Split data (50% train, 50% test)  
     X_train, X_test, y_train, y_test = train_test_split(  
         X, y, train_size=0.5, random_state=42  
     )  
     ```  
   - **Purpose**:  
     - Avoid overfitting by evaluating performance on independent test data.  

## 3. **Model Evaluation**  
   - **Training the Model**:  
     ```python  
     from sklearn.linear_model import LinearRegression  

     lm = LinearRegression(fit_intercept=True)  
     lm.fit(X_train, y_train)  # Fit on training data  
     ```  
   - **R-squared (Test Set)**:  
     ```python  
     r_squared = lm.score(X_test, y_test)  # Explains variance in test data  
     ```  
   - **MSE Calculation**:  
     ```python  
     from sklearn.metrics import mean_squared_error  

     y_pred = lm.predict(X_test)  
     test_mse = mean_squared_error(y_test, y_pred)  
     ```  

## 4. **Overfitting vs. Underfitting**  
   - **Overfitting**:  
     - **Symptoms**: Low training MSE, high test MSE.  
     - **Cause**: Model is too complex (e.g., high-degree polynomial).  
   - **Underfitting**:  
     - **Symptoms**: High training and test MSE.  
     - **Cause**: Model is too simple (e.g., linear model for nonlinear data).  
   - **Ideal Model**: Balances complexity to capture trends without fitting noise (e.g., moderate polynomial degree).  

---

### Key Takeaways:  
1. **Test MSE Over Training MSE**:  
   - Test MSE is the gold standard for assessing model generalizability.  
2. **Data Splitting**:  
   - Use `train_test_split` to isolate test data and avoid data leakage.  
3. **R-squared Context**:  
   - High R-squared on test data indicates strong predictive power.  
4. **Model Complexity Trade-off**:  
   - Flexible models risk overfitting; simple models risk underfitting. Use cross-validation to find optimal complexity.  
5. **Practical Workflow**:  
   - Split data → Train model → Evaluate on test set → Iterate based on performance.  