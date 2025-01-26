---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-typing, mutability, object-identity, references]  
---

# Summary

## 1. **Dynamic Typing Basics**  
   - **Description**: Python infers types at runtime (not compile time).  
   - **Variable-Object-Reference Model**:  
     1. Variables are references to objects.  
     2. Objects have types (e.g., `int`, `list`).  
   - **Example**:  
     ```python  
     x = 3  # Creates int object 3 and links variable x to it  
     y = x  # y references the same object as x  
     y = y - 1  # Creates new int object 2; y now references 2  
     ```

## 2. **Mutable vs. Immutable Objects**  
   - **Immutable**: Cannot change after creation (e.g., `int`, `str`, `tuple`).  
   - **Mutable**: Can modify in-place (e.g., `list`, `dict`).  
   - **Example (Mutable Behavior)**:  
     ```python  
     L1 = [2, 3, 4]  
     L2 = L1          # Both reference the same list  
     L1[0] = 24       # Modifies the shared list  
     print(L2)        # Output: [24, 3, 4]  
     ```

## 3. **Object Identity vs. Equality**  
   - **`==`**: Checks if values are equal.  
   - **`is`**: Checks if two variables reference the same object (identity).  
   - **Example**:  
     ```python  
     L = [1, 2, 3]  
     M = [1, 2, 3]  
     print(L == M)   # Output: True (same content)  
     print(L is M)   # Output: False (different objects)  
     print(id(L))    # Unique memory address for L  
     print(id(M))    # Different address for M  
     ```

## 4. **Creating Copies of Mutable Objects**  
   - **Shallow Copy**: Creates a new object with the same content.  
   - **Methods**:  
     - `list()` constructor: `M = list(L)`  
     - Slicing: `M = L[:]`  
   - **Example**:  
     ```python  
     L = [1, 2, 3]  
     M = list(L)     # New list with same content  
     print(M is L)   # Output: False  
     ```

---

### Key Takeaways:  
1. **Dynamic Typing**: Variables reference objects; types resolved at runtime.  
2. **Mutability Matters**:  
   - Immutable objects (e.g., `int`) create new objects on modification.  
   - Mutable objects (e.g., `list`) allow in-place changes (affects all references).  
3. **Identity vs. Equality**:  
   - Use `==` to compare values.  
   - Use `is` to check if variables reference the same object.  
4. **Copying Objects**: Use `list()` or slicing to avoid unintended side effects with mutable objects.  