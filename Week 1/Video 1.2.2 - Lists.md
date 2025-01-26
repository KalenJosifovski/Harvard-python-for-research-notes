---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-lists, mutability, methods, operations]  
---

# Summary

## 1. **List Basics**  
   - **Mutability**: Lists can be modified after creation (add/remove/reorder elements).  
   - **Heterogeneous Elements**: Can store any data type (e.g., `[2, "a", 3.14]`).  
   - **Indexing/Slicing**: Same as other sequences (zero-based, negative indices).  
   - **Example**:  
     ```python  
     numbers = [2, 4, 6, 8]  
     print(numbers[0])    # Output: 2  
     print(numbers[-1])   # Output: 8 (last element)  
     ```

## 2. **Common List Methods**  
   - **`.append()`**: Add an element to the end.  
   - **`.reverse()`**: Reverse the list **in-place**.  
   - **`.sort()`**: Sort the list **in-place** (alphabetical/numerical order).  
   - **Examples**:  
     ```python  
     numbers.append(10)   # List becomes [2, 4, 6, 8, 10]  
     numbers.reverse()    # List becomes [10, 8, 6, 4, 2]  
     names = ["Zofia", "Alex", "Morgan", "Anthony"]  
     names.sort()         # Sorted to ["Alex", "Anthony", "Morgan", "Zofia"]  
     ```

## 3. **List Operations**  
   - **Concatenation**: `+` merges two lists into a new list.  
   - **Repetition**: `*` repeats elements.  
   - **Example**:  
     ```python  
     x = [12, 14, 16]  
     combined = numbers + x  # Result: [2, 4, 6, 8, 12, 14, 16]  
     repeated = [1, 2] * 3   # Result: [1, 2, 1, 2, 1, 2]  
     ```

## 4. **Built-in Functions**  
   - **`sorted()`**: Returns a **new sorted list** without modifying the original.  
   - **`len()`**: Returns the number of elements.  
   - **Example**:  
     ```python  
     reversed_names = ["Zofia", "Morgan", "Anthony", "Alex"]  
     sorted_names = sorted(reversed_names)  # New list: ["Alex", "Anthony", "Morgan", "Zofia"]  
     print(len(sorted_names))               # Output: 4  
     ```

## 5. **Lists vs. Strings**  
   - **Mutability**:  
     - Lists: Mutable (can change elements).  
     - Strings: Immutable (cannot modify after creation).  
   - **Methods**:  
     - List methods (e.g., `append()`, `sort()`) modify the original list.  
     - String methods (e.g., `upper()`, `replace()`) return new strings.  

---

### Key Takeaways:  
1. **In-place vs. New Objects**:  
   - `.reverse()`, `.sort()` modify the original list.  
   - `sorted()` creates a new list.  
2. **Concatenation requires lists**: `list1 + list2` (not mixed types).  
3. **Heterogeneous storage**: Lists can hold any combination of data types.  
4. **Common use cases**: Staging dynamic data (e.g., user inputs, results from loops).  