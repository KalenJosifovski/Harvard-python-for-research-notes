---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-tuples, immutability, packing-unpacking, sequences]  
---

# Summary

## 1. **Tuple Basics**  
   - **Immutable**: Cannot modify after creation.  
   - **Heterogeneous Data**: Stores mixed types (e.g., `(1, "a", 3.14)`).  
   - **Syntax**: Elements separated by commas, often enclosed in parentheses.  
   - **Example**:  
     ```python  
     T = (1, 3, 5, 7)  
     print(type(T))  # Output: <class 'tuple'>  
     ```

## 2. **Tuple Operations**  
   - **Concatenation**: `+` creates a new tuple.  
   - **Indexing/Slicing**: Same as lists/strings (zero-based).  
   - **Length**: `len()` returns the number of elements.  
   - **Example**:  
     ```python  
     T1 = (1, 3)  
     T2 = (5, 7)  
     combined = T1 + T2  # Output: (1, 3, 5, 7)  
     print(combined[1])   # Output: 3  
     print(len(T1))       # Output: 2  
     ```

## 3. **Packing and Unpacking**  
   - **Packing**: Combining values into a tuple.  
   - **Unpacking**: Assigning tuple elements to variables.  
   - **Examples**:  
     ```python  
     # Packing  
     coordinates = (4.5, 2.8)  

     # Unpacking  
     x, y = coordinates  
     print(x)  # Output: 4.5  
     print(y)  # Output: 2.8  

     # Unpacking in loops  
     coordinates_list = [(1, 2), (3, 4), (5, 6)]  
     for (a, b) in coordinates_list:  
         print(a + b)  # Output: 3, 7, 11  
     ```

## 4. **Single-Element Tuples**  
   - **Syntax**: Requires a trailing comma to distinguish from regular parentheses.  
   - **Example**:  
     ```python  
     not_a_tuple = (2)     # Type: int  
     actual_tuple = (2,)   # Type: tuple  
     print(type(actual_tuple))  # Output: <class 'tuple'>  
     ```

## 5. **Use Cases**  
   - **Return Multiple Values**: Functions can return tuples.  
   - **Fixed Data**: Safely store unchangeable data (e.g., coordinates, configurations).  
   - **Example**:  
     ```python  
     def min_max(numbers):  
         return (min(numbers), max(numbers))  
     result = min_max([3, 1, 4])  
     print(result)  # Output: (1, 4)  
     ```

---

### Key Takeaways:  
1. **Immutability**: Tuples cannot be modified after creation (no `.append()`, `.sort()`, etc.).  
2. **Packing/Unpacking**: Simplify handling multiple return values or grouped data.  
3. **Single-Element Syntax**: Always include a comma (e.g., `(2,)`).  
4. **Performance**: Tuples are faster than lists for fixed data due to immutability.  
5. **Clarity**: Use parentheses for readability, even though they’re optional.  