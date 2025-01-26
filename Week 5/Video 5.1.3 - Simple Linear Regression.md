---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [regression, linear-regression, least-squares]  
---

# Summary

## 1. **Model Formulation**  
   - **Equation**:  
     \[ Y = \beta_0 + \beta_1 X + \epsilon \]  
     - \( Y \): Quantitative response (random variable).  
     - \( X \): Predictor variable (random variable).  
     - \( \beta_0, \beta_1 \): Model coefficients (intercept and slope).  
     - \( \epsilon \): Error term (random noise).  

## 2. **Parameter Estimation**  
   - **Goal**: Estimate \( \beta_0 \) and \( \beta_1 \) using observed data.  
   - **Data Structure**:  
     - \( n \) observation pairs: \( (x_1, y_1), (x_2, y_2), \dots, (x_n, y_n) \).  
   - **Method**: Minimize the **Residual Sum of Squares (RSS)**.  
     \[ \text{RSS} = \sum_{i=1}^n (y_i - \hat{y}_i)^2 \]  
     - **Residual**: \( e_i = y_i - \hat{y}_i \) (difference between observed and predicted values).  
     - **Least Squares**: Coefficients \( \hat{\beta}_0 \), \( \hat{\beta}_1 \) are chosen to minimize RSS.  

## 3. **Prediction**  
   - **Equation**:  
     \[ \hat{y} = \hat{\beta}_0 + \hat{\beta}_1 x \]  
     - \( \hat{y} \): Predicted value of \( Y \) for a given \( x \).  
     - \( \hat{\beta}_0, \hat{\beta}_1 \): Estimated coefficients from training data.  

## 4. **Implementation Example**  
   - **Python (scikit-learn)**:  
     ```python  
     from sklearn.linear_model import LinearRegression  
     import numpy as np  

     # Sample data  
     X = np.array([1, 2, 3, 4, 5]).reshape(-1, 1)  # Predictor  
     y = np.array([2, 4, 5, 4, 5])                 # Response  

     # Fit model  
     model = LinearRegression()  
     model.fit(X, y)  

     # Coefficients  
     beta0_hat = model.intercept_    # Estimated intercept  
     beta1_hat = model.coef_[0]      # Estimated slope  
     ```  

---

### Key Takeaways:  
1. **Core Equation**:  
   - Simple linear regression models \( Y \) as a linear function of \( X \), plus error.  
2. **Estimation Method**:  
   - Coefficients are estimated by minimizing the sum of squared residuals (RSS).  
3. **Prediction**:  
   - Use \( \hat{y} = \hat{\beta}_0 + \hat{\beta}_1 x \) to predict outcomes for new \( x \).  
4. **Practical Tools**:  
   - Libraries like `scikit-learn` automate coefficient estimation and prediction.  
5. **Residual Interpretation**:  
   - Residuals quantify prediction errors; smaller RSS indicates better model fit.  