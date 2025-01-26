---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [pandas, data-structures, indexing]  
---

# Summary

## 1. **Pandas Series**  
   - **Syntax**:  
     ```python  
     import pandas as pd  
     # Create Series from list  
     x = pd.Series([6, 3, 8, 6], index=["q", "w", "e", "r"])  
     ```  
   - **Description**:  
     - One-dimensional labeled array with explicit indexing.  
     - Default index (0-based) used if not specified.  
   - **Dictionary Input**:  
     ```python  
     ages = {"Tim": 32, "Jim": 28, "Pam": 25, "Sam": 30}  
     x = pd.Series(ages)  # Keys become indices  
     ```  

## 2. **Pandas DataFrame**  
   - **Syntax**:  
     ```python  
     data = {  
         "name": ["Tim", "Jim", "Pam", "Sam"],  
         "age": [32, 28, 25, 30],  
         "zip": [90210, 10001, 30301, 94103]  
     }  
     df = pd.DataFrame(data, columns=["name", "age", "zip"])  
     ```  
   - **Description**:  
     - Tabular data structure with row and column indices.  
     - Columns can be accessed via attribute or dictionary notation:  
       ```python  
       df.name  # Equivalent to df["name"]  
       ```  

## 3. **Indexing and Re-indexing**  
   - **Index Selection**:  
     ```python  
     x["w"]          # Access value at index "w"  
     x[["r", "w"]]   # Access multiple indices  
     ```  
   - **Re-indexing**:  
     ```python  
     new_index = ["a", "q", "w", "e"]  
     x_reindexed = x.reindex(new_index)  # Reorders data, introduces NaN for missing indices  
     ```  

## 4. **Arithmetic Operations**  
   - **Alignment by Index**:  
     ```python  
     x = pd.Series([6, 3, 8, 6], index=["q", "w", "e", "r"])  
     y = pd.Series([7, 3, 5, 2], index=["e", "q", "r", "t"])  
     x + y  # Result: e=15, q=9, r=8, t=NaN, w=NaN  
     ```  
   - **NaN Handling**:  
     - Mismatched indices result in `NaN` values.  

---

### Key Takeaways:  
1. **Series vs. DataFrame**:  
   - Use `Series` for 1D data with labels; `DataFrame` for 2D tabular data.  
2. **Index Flexibility**:  
   - Custom indices improve data accessibility and alignment.  
3. **Data Alignment**:  
   - Arithmetic operations align data by index, similar to database joins.  
4. **Practical Use Cases**:  
   - Ideal for structured data manipulation (e.g., whisky flavor datasets, demographic data).  