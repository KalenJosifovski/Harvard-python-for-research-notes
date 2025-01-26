---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-sequences, indexing, slicing, lists-tuples]  
---

# Summary

## 1. **Sequence Types**  
   - **Basic Types**:  
     - **Lists**: Mutable (`[1, 2, 3]`).  
     - **Tuples**: Immutable (`(1, 2, 3)`).  
     - **Range Objects**: Immutable sequences of numbers (`range(5)`).  
     - **Strings**: Immutable character sequences (`"Python"`).  
   - **Example**:  
     ```python  
     my_list = [1, "a", 3.14]  # List  
     my_tuple = (4, 5, 6)      # Tuple  
     my_range = range(3)       # Range (0, 1, 2)  
     my_str = "Hello"          # String  
     ```

## 2. **Indexing**  
   - **Zero-Based**: First element at index `0`.  
   - **Negative Indices**: Access elements from the end (`-1` = last element).  
   - **Examples**:  
     ```python  
     s = ["a", "b", "c", "d"]  
     print(s[0])    # Output: "a"  
     print(s[-1])   # Output: "d" (last element)  
     print(s[-2])   # Output: "c" (second last)  
     ```

## 3. **Slicing**  
   - **Syntax**: `sequence[start:stop]` (stop index is exclusive).  
   - **Behavior**: Returns a new sequence without modifying the original.  
   - **Examples**:  
     ```python  
     s = [0, 1, 2, 3, 4]  
     print(s[1:3])    # Output: [1, 2] (elements at indices 1 and 2)  
     print(s[:3])     # Output: [0, 1, 2] (from start to index 2)  
     print(s[2:])     # Output: [2, 3, 4] (from index 2 to end)  
     print(s[-3:-1])  # Output: [2, 3] (indices -3 and -2)  
     ```

## 4. **Common Sequence Operations**  
   - **Membership Testing**: `in` keyword.  
   - **Concatenation**: `+` operator.  
   - **Repetition**: `*` operator.  
   - **Length**: `len(sequence)`.  
   - **Examples**:  
     ```python  
     s = [1, 2, 3]  
     print(2 in s)          # Output: True  
     print(s + [4, 5])      # Output: [1, 2, 3, 4, 5]  
     print(s * 2)           # Output: [1, 2, 3, 1, 2, 3]  
     print(len(s))          # Output: 3  
     ```

---

### Key Takeaways:  
1. **Zero-based indexing**: First element is always `[0]`.  
2. **Negative indices** simplify accessing elements from the end.  
3. **Slicing** uses `[start:stop]` and excludes the `stop` index.  
4. **Sequence immutability**: Tuples, ranges, and strings cannot be modified after creation.  
5. **Type distinctions**:  
   - Lists: Mutable, general-purpose.  
   - Tuples: Immutable, often used for fixed data.  
   - Strings: Immutable, text manipulation.  