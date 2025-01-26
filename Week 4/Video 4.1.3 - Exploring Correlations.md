---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [pandas, data-analysis, visualization]  
---

# Summary

## 1. **Computing Flavor Correlations**  
   - **Syntax**:  
     ```python  
     corr_flavors = flavors.corr()  # Pearson correlation matrix for flavor attributes  
     ```  
   - **Description**:  
     - Calculates pairwise Pearson correlations between 12 flavor attributes (e.g., Body, Smoky, Sweet).  
     - Values range from -1 (perfect inverse) to +1 (perfect positive correlation).  

## 2. **Visualizing Correlation Matrix**  
   - **Syntax**:  
     ```python  
     import matplotlib.pyplot as plt  
     plt.figure(figsize=(10, 10))  
     plt.pcolor(corr_flavors, cmap="coolwarm")  
     plt.colorbar()  
     plt.axis("tight")  # Adjusts axes to data range  
     plt.savefig("flavor_correlations.pdf")  
     ```  
   - **Key Findings**:  
     - Strong positive correlation between `Body` and `Smoky` (e.g., heavy-bodied whiskies tend to be smoky).  
     - Negative correlation between `Floral` and `Medicinal` flavors.  

## 3. **Whisky-to-Whisky Correlations**  
   - **Syntax**:  
     ```python  
     corr_whisky = flavors.T.corr()  # Transpose to correlate whiskies (86x86 matrix)  
     ```  
   - **Visualization**:  
     ```python  
     plt.figure(figsize=(10, 10))  
     plt.pcolor(corr_whisky, cmap="coolwarm")  
     plt.axis("tight")  # Removes whitespace for 86x86 matrix  
     plt.savefig("whisky_correlations.pdf")  
     ```  
   - **Insight**:  
     - Reveals flavor profile similarities between distilleries (e.g., whiskies with similar scores across all 12 attributes).  

---

### Key Takeaways:  
1. **Pearson Correlation**:  
   - Measures linear relationships between variables. Use `.corr()` for quick analysis.  
2. **Heatmap Interpretation**:  
   - Warm colors (red) = positive correlations; cool colors (blue) = negative correlations.  
3. **Transpose for Distillery Analysis**:  
   - Correlate whiskies (rows) instead of flavors (columns) by transposing the DataFrame.  
4. **Practical Applications**:  
   - Identify flavor clusters for product development or market segmentation.  