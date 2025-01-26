---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [data-cleaning, visualization, pandas]  
---

# Summary

## 1. **Handling NaN Values in Speed Data**  
   - **Issue**: NaN (Not a Number) entries in the speed array prevent histogram plotting.  
   - **Detection**:  
     ```python  
     import numpy as np  
     # Check for NaNs  
     nan_mask = np.isnan(speed_data)  
     nan_count = np.sum(nan_mask)  # Total NaNs  
     clean_speed = speed_data[~nan_mask]  # Exclude NaNs  
     ```  
   - **Example**:  
     ```python  
     print(f"Number of NaNs: {nan_count}")  
     # Output: "Number of NaNs: 85" (for Eric's data)  
     ```

## 2. **Custom Histogram with Matplotlib**  
   - **Syntax**:  
     ```python  
     import matplotlib.pyplot as plt  
     plt.hist(clean_speed,  
              bins=np.linspace(0, 30, 20),  # 20 bins between 0-30  
              density=True,                  # Normalize to probability density  
              edgecolor='black')  
     plt.xlabel("Speed (m/s)")  
     plt.ylabel("Probability Density")  
     plt.title("Eric's Flight Speed Distribution")  
     plt.savefig("custom_histogram.pdf")  
     plt.show()  
     ```  
   - **Key Features**:  
     - Explicit NaN removal.  
     - Custom bin edges and normalization.  

## 3. **Simplified Histogram with Pandas**  
   - **Syntax**:  
     ```python  
     import pandas as pd  
     # Plot directly from DataFrame (auto-handles NaNs)  
     bird_data['speed_2D'].plot.hist(bins=20,  
                                     range=(0, 30),  
                                     density=True,  
                                     title="Pandas Histogram")  
     plt.savefig("pd_hist.pdf")  
     ```  
   - **Advantage**: Automatically ignores NaNs without manual filtering.  

---

### Key Takeaways:  
1. **NaN Management**:  
   - Always check for NaNs using `np.isnan()` before plotting.  
   - Use boolean indexing (`~nan_mask`) to filter invalid data.  
2. **Visualization Flexibility**:  
   - Matplotlib allows granular control (bins, labels, normalization).  
   - Pandas simplifies plotting but offers fewer customization options.  
3. **Efficiency**:  
   - Pandas `plot.hist()` is quicker for exploratory analysis.  
   - Matplotlib is preferred for publication-quality figures.  
4. **Domain Context**:  
   - Speed values are 2D approximations (local earth surface projection).  
   - Biologically implausible speeds may indicate data errors.  