---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [numpy, array-indexing, boolean-masking]  
---

# Summary

## 1. **Indexing with Arrays/Lists**  
   - **Syntax**: Use lists or NumPy arrays as indices to select specific elements.  
   - **Description**: Allows non-contiguous or custom element selection.  
   - **Example**:  
     ```python  
     import numpy as np  
     z1 = np.array([1, 3, 5, 7, 9])  
     ind = [0, 2, 3]                # Index list  
     print(z1[ind])                  # Output: [1, 5, 7]  
     # Using a NumPy array as an index  
     ind_arr = np.array([1, 4])  
     print(z1[ind_arr])              # Output: [3, 9]  
     ```

## 2. **Boolean (Logical) Indexing**  
   - **Syntax**: Use boolean arrays to filter elements based on conditions.  
   - **Description**: Returns elements where the boolean array is `True`.  
   - **Example**:  
     ```python  
     # Create a boolean mask  
     mask = z1 > 6  
     print(mask)                     # Output: [False, False, False, True, True]  
     print(z1[mask])                 # Output: [7, 9]  
     # Apply mask to another array  
     z2 = z1 + 1  
     print(z2[mask])                 # Output: [8, 10]  
     ```

## 3. **Slicing vs. Indexing Behavior**  
   - **Syntax**:  
     - **Slicing** (`:`) creates a **view** (modifications affect the original array).  
     - **Indexing** (lists/arrays) creates a **copy** (modifications do not affect the original).  
   - **Examples**:  
     ```python  
     # Slicing (view)  
     w_slice = z1[0:3]              # Slice z1  
     w_slice[0] = 100               # Modifies original z1  
     print(z1)                      # Output: [100, 3, 5, 7, 9]  
     # Indexing (copy)  
     w_copy = z1[[0, 1, 2]]         # Copy via indexing  
     w_copy[0] = 200                # Does NOT modify z1  
     print(z1)                      # Output remains [100, 3, 5, 7, 9]  
     ```

---

### Key Takeaways:  
1. **Indexing Flexibility**:  
   - Use lists, arrays, or boolean masks to access elements.  
2. **Boolean Masking**:  
   - Filter elements dynamically using logical conditions (e.g., `z1 > 6`).  
3. **View vs. Copy**:  
   - **Slicing** creates a **view** → Changes propagate to the original array.  
   - **Indexing** creates a **copy** → Changes are isolated.  
4. **Efficiency**:  
   - Boolean indexing is powerful for conditional data extraction.  