---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [copy-module, shallow-deep-copy, mutable-objects]  
---

# Summary

## 1. **Copy Types**  
   - **Shallow Copy**:  
     - Creates a new object but retains references to nested objects from the original.  
     - Syntax: `copy.copy(original)` or `list.copy()` for lists.  
   - **Deep Copy**:  
     - Creates a new object and recursively copies all nested objects.  
     - Syntax: `copy.deepcopy(original)`.  

## 2. **Shallow vs. Deep Copy**  
   - **Shallow Copy**:  
     ```python  
     import copy  
     original = [[1, 2], [3, 4]]  
     shallow = copy.copy(original)  
     original[0][0] = 99  
     print(shallow)  # Output: [[99, 2], [3, 4]] (shared nested objects)  
     ```  
   - **Deep Copy**:  
     ```python  
     deep = copy.deepcopy(original)  
     original[0][0] = 100  
     print(deep)     # Output: [[99, 2], [3, 4]] (independent nested objects)  
     ```  

## 3. **When to Use**  
   - **Shallow Copy**:  
     - Suitable for simple, flat structures (no nested mutable objects).  
   - **Deep Copy**:  
     - Required for complex structures with nested mutable objects (e.g., lists of lists).  

---

### Key Takeaways:  
1. **Shallow Copies** are memory-efficient but share nested objects with the original.  
2. **Deep Copies** ensure full independence but are computationally heavier.  
3. **Use Cases**:  
   - Shallow: Cloning configurations or simple data structures.  
   - Deep: Duplicating nested data (e.g., matrices, JSON-like structures).  
4. **Pitfall**: Modifying nested objects in a shallow copy affects the original.  