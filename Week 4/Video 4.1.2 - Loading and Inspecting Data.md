---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [pandas, data-import, data-inspection]  
---

# Summary

## 1. **Loading Data with Pandas**  
   - **Syntax**:  
     ```python  
     import pandas as pd  
     import numpy as np  
     # Load whiskies data  
     whisky = pd.read_csv("whiskies.txt")  
     # Add region data as a new column  
     whisky["Region"] = pd.read_csv("regions.txt")  
     ```  
   - **Description**:  
     - `whiskies.txt` contains whisky attributes; `regions.txt` specifies production regions.  
     - Combined into a single DataFrame with a "Region" column.  

## 2. **Inspecting Data**  
   - **Syntax**:  
     ```python  
     whisky.head()   # First 5 rows  
     whisky.tail()   # Last 5 rows  
     whisky.iloc[5:10, 0:5]  # Rows 5-9, columns 0-4  
     ```  
   - **Description**:  
     - Use `head()`/`tail()` for quick overviews.  
     - `iloc` indexes by integer position for precise slicing.  

## 3. **Identifying Columns**  
   - **Syntax**:  
     ```python  
     print(whisky.columns)  # List all column names  
     ```  
   - **Output**:  
     - Columns include metadata (e.g., "Distillery") and flavor attributes (e.g., "Body", "Smoky", "Floral").  

## 4. **Extracting Flavor Attributes**  
   - **Syntax**:  
     ```python  
     flavors = whisky.iloc[:, 2:14]  # Columns 2-13 (Body to Floral)  
     ```  
   - **Description**:  
     - Slice columns 2-13 to isolate flavor scores (0-4 scale across 12 categories).  

---

### Key Takeaways:  
1. **CSV Handling**:  
   - Use `pd.read_csv()` even for `.txt` files if data is comma-separated.  
2. **Data Verification**:  
   - Always inspect data with `head()`, `tail()`, and `iloc` after loading.  
3. **Column Management**:  
   - Extract subsets of columns using `iloc` for focused analysis (e.g., flavor profiles).  
4. **Metadata Integration**:  
   - Add region data as a column to link geographical information with flavor attributes.  