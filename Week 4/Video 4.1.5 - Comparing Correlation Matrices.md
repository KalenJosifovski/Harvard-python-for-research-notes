---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [clustering, data-visualization, pandas]  
---

# Summary

## 1. **Appending Cluster Labels**  
   - **Syntax**:  
     ```python  
     # Add cluster labels to the whisky DataFrame  
     whisky["Cluster"] = model.row_labels_  
     ```  
   - **Description**:  
     - Attaches spectral co-clustering results (cluster IDs 0-5) as a new column.  
     - Enables sorting and grouping by cluster membership.  

## 2. **Reordering Data by Clusters**  
   - **Syntax**:  
     ```python  
     # Sort DataFrame by cluster labels and reset index  
     whisky_sorted = whisky.sort_values("Cluster").reset_index(drop=True)  
     ```  
   - **Description**:  
     - Rearranges whiskies to group those in the same cluster consecutively.  

## 3. **Recalculating Correlations**  
   - **Syntax**:  
     ```python  
     # Extract flavor attributes and transpose  
     flavors_sorted = whisky_sorted.iloc[:, 2:14].T  
     # Compute new correlation matrix and convert to NumPy array  
     correlations = flavors_sorted.corr().to_numpy()  
     ```  
   - **Purpose**:  
     - Updates correlation matrix to reflect cluster-based ordering.  

## 4. **Visualizing Original vs. Reordered Matrices**  
   - **Syntax**:  
     ```python  
     import matplotlib.pyplot as plt  
     # Plot original correlation matrix  
     plt.subplot(1, 2, 1)  
     plt.pcolor(corr_whisky, cmap="coolwarm")  
     plt.title("Original")  
     # Plot reordered correlation matrix  
     plt.subplot(1, 2, 2)  
     plt.pcolor(correlations, cmap="coolwarm")  
     plt.title("Clustered")  
     plt.savefig("correlation_comparison.pdf")  
     ```  
   - **Output**:  
     - Left: Original 86x86 whisky correlation matrix.  
     - Right: Block-diagonal structure showing 6 clusters along the diagonal.  

---

### Key Takeaways:  
1. **Cluster Visualization**:  
   - Reordering the correlation matrix reveals distinct blocks, validating the spectral co-clustering results.  
2. **Data Alignment**:  
   - Sorting by cluster labels groups similar whiskies, simplifying pattern detection.  
3. **Practical Insight**:  
   - Blocks indicate whiskies with shared flavor profiles (e.g., smoky Islay whiskies grouped together).  
4. **Technical Note**:  
   - Converting to a NumPy array (`to_numpy()`) ensures compatibility with visualization tools like `pcolor`.  