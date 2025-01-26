---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-errors, debugging, best-practices]  
---

# Summary

## 1. **List Index Out of Range**  
   - **Syntax**: Accessing non-existent indices in a list.  
   - **Description**: Lists are zero-indexed; ensure indices are within `0` to `len(list)-1`.  
   - **Example**:  
     ```python  
     L = [1, 2, 3]  
     print(L[3])  # Error: Index 3 is out of bounds (valid indices: 0, 1, 2)  
     ```

## 2. **Dictionary Key Misuse**  
   - **Syntax**: Accessing keys with incorrect types or non-existent keys.  
   - **Description**: Dictionary keys must match the exact type and value.  
   - **Example**:  
     ```python  
     D = {"1": "aa", "2": "bb"}  
     print(D[1])    # KeyError (key is string "1", not integer 1)  
     print(D["1"])  # Correct: "aa"  
     ```

## 3. **Unsupported Object Operations**  
   - **Syntax**: Using invalid methods for an object type.  
   - **Description**: Verify object types and their supported methods.  
   - **Example**:  
     ```python  
     L = [2, 4, 6]  
     L.add(8)     # AttributeError (use L.append(8) instead)  
     ```

## 4. **Modifying Immutable Objects**  
   - **Syntax**: Attempting to change immutable objects like strings.  
   - **Description**: Use mutable alternatives (e.g., lists) if modifications are needed.  
   - **Example**:  
     ```python  
     s = "Python"  
     s[0] = "J"  # TypeError (strings are immutable)  
     ```

## 5. **Type Mismatch Errors**  
   - **Syntax**: Combining incompatible types (e.g., string + integer).  
   - **Description**: Convert types explicitly for compatibility.  
   - **Example**:  
     ```python  
     print("Answer: " + 8)       # TypeError  
     print("Answer: " + str(8))  # Correct: "Answer: 8"  
     ```

## 6. **Indentation Errors**  
   - **Syntax**: Misplaced indentation in loops or functions.  
   - **Description**: Ensure code blocks (e.g., loops, returns) are properly indented.  
   - **Example**:  
     ```python  
     # Incorrect: Return inside loop  
     def running_sum(n):  
         rsum = 0  
         for k in range(n):  
             rsum += k  
             return rsum  # Returns immediately (indentation error)  
     # Correct: Return after loop  
     def running_sum(n):  
         rsum = 0  
         for k in range(n):  
             rsum += k  
         return rsum  
     ```

---

### Key Takeaways:  
1. **Error Messages**: Always read error messages to diagnose issues (e.g., `IndexError`, `KeyError`).  
2. **Object Types**:  
   - Know the type of objects (e.g., list vs. string).  
   - Use appropriate methods (e.g., `append()` for lists).  
3. **Immutability**: Avoid modifying immutable objects (e.g., strings, tuples).  
4. **Type Conversions**: Convert types explicitly (e.g., `str()`, `int()`) to prevent mismatches.  
5. **Indentation**: Ensure code blocks (loops, conditionals, returns) are correctly indented.  
6. **Dictionaries**:  
   - Keys are case-sensitive and type-sensitive.  
   - Prefer `.get()` to avoid `KeyError` (e.g., `D.get("key", default_value)`).  