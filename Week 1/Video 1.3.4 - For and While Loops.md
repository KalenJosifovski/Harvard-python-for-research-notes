---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-loops, for-loop, while-loop, iteration]  
---

# Summary

## 1. **For Loops**  
   - **Purpose**: Iterate over sequences (lists, tuples, dictionaries, ranges, etc.).  
   - **Syntax**:  
     ```python  
     for item in sequence:  
         # code block  
     ```  
   - **Examples**:  
     ```python  
     # Iterate over a range  
     for x in range(10):  
         print(x)  # Output: 0, 1, 2, ..., 9  

     # Iterate over a list (Pythonic approach)  
     names = ["Alice", "Bob", "Charlie"]  
     for name in names:  
         print(name)  

     # Avoid non-Pythonic index-based loops  
     for i in range(len(names)):  # Less preferred  
         print(names[i])  
     ```  

## 2. **Dictionary Iteration**  
   - **Methods**:  
     - `.keys()`: Iterate over dictionary keys.  
     - Shorthand: `for key in dict` (equivalent to `.keys()`).  
     - Sorting: Use `sorted()` for ordered iteration.  
   - **Examples**:  
     ```python  
     ages = {"Alice": 30, "Bob": 25, "Charlie": 35}  

     # Standard iteration  
     for name in ages:  
         print(f"{name}: {ages[name]}")  

     # Sorted keys (alphabetical)  
     for name in sorted(ages):  
         print(name)  

     # Reverse order  
     for name in sorted(ages, reverse=True):  
         print(name)  
     ```  

## 3. **While Loops**  
   - **Purpose**: Execute code while a condition is `True` (unknown iteration count).  
   - **Syntax**:  
     ```python  
     while condition:  
         # code block  
     ```  
   - **Example**:  
     ```python  
     count = 0  
     while count < 5:  
         print(count)  # Output: 0, 1, 2, 3, 4  
         count += 1  
     ```  

## 4. **For vs. While Loops**  
   - **For Loop**: Use when the number of iterations is known (e.g., iterating over a sequence).  
   - **While Loop**: Use when iterations depend on a dynamic condition (e.g., user input, counters).  

---

### Key Takeaways:  
1. **Pythonic Looping**: Prefer `for item in sequence` over index-based loops for readability.  
2. **Dictionary Order**:  
   - Dictionaries are unordered; use `sorted()` for ordered key iteration.  
   - Reverse sorting: `sorted(ages, reverse=True)`.  
3. **Avoid Infinite Loops**: Ensure the While Loop condition eventually becomes `False`.  
4. **Use Cases**:  
   - **For**: Lists, ranges, dictionaries, strings.  
   - **While**: Game loops, input validation, dynamic workflows.  