---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [clustering, scikit-learn, spectral-analysis]  
---

# Summary

## 1. **Spectral Co-Clustering Setup**  
   - **Syntax**:  
     ```python  
     from sklearn.cluster import SpectralCoclustering  
     model = SpectralCoclustering(n_clusters=6, random_state=0)  
     ```  
   - **Description**:  
     - Clusters rows (whiskies) and columns (flavors) simultaneously.  
     - `n_clusters=6` aligns with the six whisky-producing regions in Scotland.  

## 2. **Fitting the Model**  
   - **Syntax**:  
     ```python  
     model.fit(corr_whisky)  # corr_whisky is the 86x86 whisky correlation matrix  
     ```  
   - **Description**:  
     - Uses the whisky-flavor correlation matrix to identify clusters.  
     - Reorders rows/columns to group similar whiskies and flavors.  

## 3. **Extracting Cluster Labels**  
   - **Syntax**:  
     ```python  
     cluster_labels = model.row_labels_  # Array of cluster IDs (0-5) for each whisky  
     ```  
   - **Example**:  
     ```python  
     print(cluster_labels)  # Output: [5, 2, 1, ..., 4] (86 elements)  
     ```  

## 4. **Validating Clusters**  
   - **Cluster Sizes**:  
     ```python  
     import numpy as np  
     print(np.sum(model.rows_, axis=1))  # Count of whiskies per cluster  
     # Example output: [15, 12, 19, 10, 14, 16]  
     ```  
   - **Membership Check**:  
     ```python  
     print(np.sum(model.rows_, axis=0))  # Should return 1 for all 86 whiskies  
     # Output: [1, 1, ..., 1] (confirms each whisky belongs to exactly one cluster)  
     ```  

## 5. **Interpreting Results**  
   - **Matrix Reordering**:  
     - The algorithm reorders the correlation matrix to reveal block-diagonal patterns.  
     - Each block represents a cluster of whiskies with similar flavor profiles.  
   - **Regional Alignment**:  
     - Compare clusters to known whisky regions (e.g., Islay, Highlands) to validate groupings.  

---

### Key Takeaways:  
1. **Co-Clustering**:  
   - Groups both whiskies and flavors, unlike traditional one-way clustering.  
2. **Spectral Method**:  
   - Uses eigenvalues/eigenvectors of the correlation matrix to find optimal groupings.  
3. **Validation**:  
   - Ensure each whisky is assigned to exactly one cluster (`sum(axis=0) == 1`).  
4. **Practical Use**:  
   - Identify flavor-based market segments or optimize whisky blending strategies.  