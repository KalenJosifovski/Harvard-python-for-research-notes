---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-expressions, booleans, comparisons, operators]  
---

# Summary

## 1. **Boolean Data Type**  
   - **Values**: `True` and `False` (must be capitalized).  
   - **Example**:  
     ```python  
     print(type(True))   # Output: <class 'bool'>  
     print(type(False))  # Output: <class 'bool'>  
     ```

## 2. **Boolean Operations**  
   - **Operators**: `or`, `and`, `not`.  
   - **Truth Tables**:  
     ```python  
     print(True or False)   # Output: True  
     print(True and False)  # Output: False  
     print(not True)        # Output: False  
     ```

## 3. **Comparison Operators**  
   - **Operators**:  
     - `<`, `>`, `<=`, `>=`, `==`, `!=`, `is`, `is not` (total of 8).  
   - **Examples**:  
     ```python  
     # Numeric comparisons  
     print(2 < 4)          # Output: True  
     print(2.0 == 2)       # Output: True (int 2 → float 2.0)  

     # Sequence comparisons (element-wise)  
     list1 = [2, 3]  
     list2 = [2, 3]  
     print(list1 == list2) # Output: True (contents match)  
     print(list1 is list2) # Output: False (different objects)  
     ```

## 4. **Identity vs. Equality**  
   - **`==`**: Checks if values are equal.  
   - **`is`**: Checks if objects are identical in memory.  
   - **Example**:  
     ```python  
     a = [1, 2]  
     b = [1, 2]  
     c = a  
     print(a == b)  # Output: True  
     print(a is b)  # Output: False  
     print(a is c)  # Output: True  
     ```

## 5. **Type Handling in Comparisons**  
   - **Implicit Conversion**: Python converts operands to compatible types (e.g., `int` to `float`).  
   - **Example**:  
     ```python  
     print(2.0 == 2)     # Output: True  
     print(5 == "5")     # Output: False (no conversion between int and str)  
     ```

---

### Key Takeaways:  
1. **Capitalization matters**: `True`/`False` are keywords; `true`/`false` are invalid.  
2. **`is` vs. `==`**:  
   - `==` compares values.  
   - `is` checks if two variables reference the same object.  
3. **Element-wise comparisons** for sequences (e.g., lists, tuples).  
4. **Implicit type conversion** occurs in numeric comparisons (e.g., `int` ↔ `float`).  