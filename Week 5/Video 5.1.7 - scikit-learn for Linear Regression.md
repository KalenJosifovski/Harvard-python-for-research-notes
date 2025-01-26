---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [scikit-learn, linear-regression, synthetic-data]  
---

# Summary

## 1. **Data Generation**  
   - **Syntax**:  
     ```python  
     import numpy as np  
     import scipy.stats as ss  

     # Parameters  
     n = 500  
     beta0, beta1, beta2 = 5, 2, -1  
     np.random.seed(42)  

     # Generate predictors (X1, X2)  
     x1 = ss.uniform.rvs(size=n) * 10  # Uniform in [0,10]  
     x2 = ss.uniform.rvs(size=n) * 10  

     # Generate response (Y) with Gaussian noise  
     noise = ss.norm.rvs(loc=0, scale=1, size=n)  
     y = beta0 + beta1*x1 + beta2*x2 + noise  

     # Create feature matrix X  
     X = np.stack([x1, x2], axis=1)  
     ```  
   - **Description**:  
     - Simulates data with 2 predictors (\(X_1\), \(X_2\)) and a linear relationship: \(Y = 5 + 2X_1 - X_2 + \epsilon\).  

## 2. **Model Training**  
   - **Syntax**:  
     ```python  
     from sklearn.linear_model import LinearRegression  

     # Initialize and fit model  
     lm = LinearRegression(fit_intercept=True)  
     lm.fit(X, y)  

     # Extract coefficients  
     intercept_hat = lm.intercept_          # Estimated intercept (≈5.0)  
     beta1_hat, beta2_hat = lm.coef_        # Estimated slopes (≈2.0, ≈-1.0)  
     ```  
   - **Key Parameters**:  
     - `fit_intercept=True`: Ensures the model estimates the intercept term (\( \beta_0 \)).  

## 3. **Prediction & Evaluation**  
   - **Predict for New Data**:  
     ```python  
     # Reshape input to avoid warnings (single sample)  
     X_new = np.array([[2, 4]]).reshape(1, -1)  
     y_pred = lm.predict(X_new)             # Predicted Y (≈5.07)  
     ```  
   - **R-squared Calculation**:  
     ```python  
     r_squared = lm.score(X, y)             # Returns ~0.98  
     ```  
   - **Interpretation**:  
     - R-squared of 0.98 indicates the model explains 98% of variance in \(Y\) (high due to synthetic data).  

---

### Key Takeaways:  
1. **Intercept Inclusion**:  
   - Always set `fit_intercept=True` unless the true intercept is known to be zero.  
2. **Coefficient Interpretation**:  
   - Coefficients reflect the change in \(Y\) per unit change in a predictor, **holding others constant**.  
3. **Input Shape Handling**:  
   - Use `.reshape(1, -1)` for single-sample predictions to avoid dimension warnings.  
4. **Synthetic Data Advantage**:  
   - Coefficients closely match true values (\( \beta_0=5, \beta_1=2, \beta_2=-1 \)) due to controlled noise.  
5. **R-squared Context**:  
   - High R-squared values (e.g., 0.98) are common in synthetic datasets but rare in real-world applications.  