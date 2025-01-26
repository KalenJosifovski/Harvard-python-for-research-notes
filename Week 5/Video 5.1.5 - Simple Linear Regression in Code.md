---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [regression, statsmodels, ols, r-squared]  
---

# Summary

## 1. **Model Setup with Intercept**  
   - **Syntax**:  
     ```python  
     import statsmodels.api as sm  

     # Add intercept term (column of 1s)  
     X = sm.add_constant(x)  # x: original predictor  
     ```  
   - **Purpose**:  
     - Allows estimation of both intercept (\( \beta_0 \)) and slope (\( \beta_1 \)).  
     - Without intercept, the model forces the regression line through the origin, biasing slope estimates.  

## 2. **Fitting the Model**  
   - **Syntax**:  
     ```python  
     # Define and fit the OLS model  
     model = sm.OLS(y, X)  
     results = model.fit()  
     print(results.summary())  
     ```  
   - **Output Example**:  
     ```
     OLS Regression Results                            
     ==============================================================================
                     coef    std err          t      P>|t|      [0.025      0.975]
     ------------------------------------------------------------------------------
     const         5.2000      0.123     42.280      0.000       4.956       5.444
     x1            1.9685      0.021     93.739      0.000       1.927       2.010
     ==============================================================================
     R-squared: 0.894  
     ```  
   - **Interpretation**:  
     - **Intercept (5.2)**: Expected value of \( Y \) when \( X = 0 \).  
     - **Slope (1.9685)**: A 1-unit increase in \( X \) is associated with a ~1.97-unit increase in \( Y \).  

## 3. **Key Output Metrics**  
   - **Standard Errors**:  
     - Measure variability of coefficient estimates across hypothetical samples (e.g., slope SE = 0.021).  
   - **Confidence Intervals**:  
     - 95% CI for slope: [1.927, 2.010] (true slope = 2.0 lies within this range).  
   - **R-squared**:  
     - Proportion of variance in \( Y \) explained by \( X \) (e.g., 0.894 → 89.4% variance explained).  

## 4. **Model Diagnostics**  
   - **Sampling Distributions**:  
     - Repeated sampling would generate distributions for \( \beta_0 \) and \( \beta_1 \); their standard deviations are the standard errors.  
   - **Significance Testing**:  
     - \( p \)-values (< 0.05) indicate coefficients are statistically significant (not zero).  

---

### Key Takeaways:  
1. **Intercept Inclusion**:  
   - Always use `sm.add_constant()` to avoid biased slope estimates.  
2. **Coefficient Interpretation**:  
   - Slope: Effect size of \( X \) on \( Y \).  
   - Intercept: Baseline \( Y \) value when \( X = 0 \).  
3. **R-squared Context**:  
   - High R-squared (e.g., 0.894) indicates strong explanatory power, but domain relevance matters.  
4. **Standard Errors & Confidence Intervals**:  
   - Quantify uncertainty in estimates; narrower intervals imply higher precision.  
5. **Assumption Checks**:  
   - Validate linearity, homoscedasticity, and normality of residuals for reliable inference.  