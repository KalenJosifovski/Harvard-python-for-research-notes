---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [classification, logistic-regression, maximum-likelihood]  
---

# Summary

## 1. **Model Formulation**  
   - **Equation (Logit Function)**:  
     \[ \log\left(\frac{p(X)}{1 - p(X)}\right) = \beta_0 + \beta_1 X_1 + \dots + \beta_p X_p \]  
     - \( p(X) \): Probability that \( Y = 1 \) given predictors \( X \).  
     - **Left-hand side**: Log-odds (logit transformation).  
     - **Right-hand side**: Linear combination of predictors.  

   - **Probability Prediction**:  
     \[ p(X) = \frac{1}{1 + e^{-(\beta_0 + \beta_1 X_1 + \dots + \beta_p X_p)}} \]  
     - Ensures \( p(X) \in [0, 1] \).  

## 2. **Key Concepts**  
   - **Odds vs. Log-Odds**:  
     - **Odds**: \( \frac{p(X)}{1 - p(X)} \) (ranges from 0 to \( \infty \)).  
     - **Log-Odds**: \( \log(\text{Odds}) \) (ranges from \( -\infty \) to \( \infty \)).  
   - **Interpretation of Coefficients**:  
     - A 1-unit increase in \( X_k \) changes the log-odds by \( \beta_k \).  
     - Example: \( \beta_1 = 0.5 \) → Odds increase by \( e^{0.5} \approx 1.65 \) per unit \( X_1 \).  

## 3. **Estimation Method**  
   - **Maximum Likelihood Estimation (MLE)**:  
     - Finds \( \beta_0, \beta_1, \dots, \beta_p \) that maximize the likelihood of observing the data.  
     - Iterative algorithms (e.g., Newton-Raphson) are used for optimization.  

## 4. **Implementation Example (scikit-learn)**  
   - **Syntax**:  
     ```python  
     from sklearn.linear_model import LogisticRegression  
     import numpy as np  

     # Sample data (binary classification)  
     X = np.array([[1.2], [2.4], [3.1], [4.8]])  # Predictor  
     y = np.array([0, 0, 1, 1])                   # Response (0 or 1)  

     # Fit model  
     model = LogisticRegression()  
     model.fit(X, y)  

     # Predict probabilities  
     prob_class1 = model.predict_proba(X)[:, 1]  # P(Y=1 | X)  
     ```  
   - **Output**:  
     - Coefficients: `model.coef_` (slopes), `model.intercept_` (intercept).  
     - Class probabilities: `prob_class1` returns values between 0 and 1.  

---

### Key Takeaways:  
1. **Binary Classification**:  
   - Logistic regression predicts probabilities for binary outcomes (0/1).  
2. **Logit Transformation**:  
   - Constrains probabilities to [0,1] while maintaining a linear relationship with predictors.  
3. **Coefficient Interpretation**:  
   - Coefficients represent changes in log-odds, not direct probabilities.  
4. **Practical Use**:  
   - Use `LogisticRegression` in `scikit-learn` for efficient implementation.  
5. **Model Diagnostics**:  
   - Evaluate with metrics like accuracy, ROC-AUC, or confusion matrices.  