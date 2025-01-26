---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-sets, uniqueness, set-operations, hashable]  
---

# Summary

## 1. **Set Basics**  
   - **Unordered & Unique**: Contains distinct, hashable elements (no duplicates).  
   - **Types**:  
     - **Mutable Set**: `set()` (supports additions/removals).  
     - **Immutable Set**: `frozenset()` (fixed after creation).  
   - **Syntax**: Use curly braces `{ }` or `set()` constructor.  
   - **Example**:  
     ```python  
     numbers = {1, 2, 3}  
     empty_set = set()  
     ```

## 2. **Set Operations**  
   - **Add Elements**: `.add()` inserts a new element (ignores duplicates).  
   - **Remove Elements**: `.pop()` removes and returns an arbitrary element.  
   - **Example**:  
     ```python  
     ids = {1, 2, 4, 6, 7, 8, 9}  
     ids.add(10)        # Adds 10 → {1, 2, 4, 6, 7, 8, 9, 10}  
     ids.add(2)         # No change (duplicate)  
     removed = ids.pop()# Removes random element (e.g., 1)  
     ```

## 3. **Mathematical Set Operations**  
   - **Union (`|`)**: Combine elements from both sets.  
   - **Intersection (`&`)**: Elements common to both sets.  
   - **Difference (`-`)**: Elements in set A not in set B.  
   - **Example**:  
     ```python  
     males = {0, 1, 2, 3}  
     females = {4, 5, 6, 7, 8, 9}  
     everyone = males | females  # Union → {0,1,2,3,4,5,6,7,8,9}  
     common = males & {1, 2, 3}  # Intersection → {1, 2, 3}  
     ```

## 4. **Practical Applications**  
   - **Count Unique Elements**: Convert a sequence to a set.  
   - **Example**:  
     ```python  
     word = "antidisestablishmentarianism"  
     unique_letters = set(word)  
     print(len(unique_letters))  # Output: 12  
     ```

## 5. **Key Restrictions**  
   - **Hashable Elements**: Sets cannot store mutable objects (e.g., lists).  
   - **No Indexing**: Elements are unordered (cannot use `[index]`).  
   - **Example**:  
     ```python  
     # invalid_set = {[1, 2]} → TypeError (list is unhashable)  
     ```

---

### Key Takeaways:  
1. **Uniqueness**: Sets automatically eliminate duplicates.  
2. **Efficiency**: Fast membership testing (`in` keyword) and set operations.  
3. **Mutability**: Use `frozenset()` for immutable sets (e.g., as dictionary keys).  
4. **Use Cases**:  
   - Remove duplicates from a list: `list(set(my_list))`.  
   - Mathematical operations (union, intersection).  
   - Tracking unique items (e.g., user IDs, words).  