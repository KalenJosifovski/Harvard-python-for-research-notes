---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-dictionaries, key-value, mutability, view-objects]  
---

# Summary

## 1. **Dictionary Basics**  
   - **Key-Value Pairs**: Keys are immutable (e.g., `str`, `int`, `tuple`); values can be any type.  
   - **Mutable**: Modify/add/remove entries after creation.  
   - **Unordered**: No guaranteed order during iteration.  
   - **Example**:  
     ```python  
     age = {"Pam": 30, "Tim": 25, "Nick": 31}  
     ```

## 2. **Creating Dictionaries**  
   - **Empty Dictionary**: Use `{}` or `dict()`.  
   - **Adding Entries**: Assign values to new/existing keys.  
   - **Example**:  
     ```python  
     empty_dict = {}  
     age = dict()  
     age["Tom"] = 50  # Adds new key-value pair  
     ```

## 3. **Accessing & Modifying Values**  
   - **Lookup**: Use `dict[key]`.  
   - **Update Values**: Modify directly or use shorthand operators like `+=`.  
   - **Example**:  
     ```python  
     print(age["Tim"])    # Output: 25  
     age["Tim"] += 1      # Increment Tim's age → 26  
     ```

## 4. **View Objects**  
   - **`.keys()`**: Returns dynamic view of keys.  
   - **`.values()`**: Returns dynamic view of values.  
   - **Dynamic Updates**: Views reflect changes to the dictionary.  
   - **Example**:  
     ```python  
     names = age.keys()  
     print(names)        # Output: dict_keys(['Pam', 'Tim', 'Nick', 'Tom'])  
     age["Zoe"] = 28  
     print(names)        # Updated to include 'Zoe'  
     ```

## 5. **Membership Testing**  
   - **Check Key Existence**: Use `in` operator.  
   - **Example**:  
     ```python  
     print("Tom" in age)  # Output: True  
     print("Zofia" in age) # Output: False  
     ```

## 6. **Iterating Over Dictionaries**  
   - **Unordered Iteration**: Order not guaranteed.  
   - **Example**:  
     ```python  
     for key in age:  
         print(f"{key}: {age[key]}")  # Output varies (e.g., "Pam: 30", "Tim: 26", etc.)  
     ```

---

### Key Takeaways:  
1. **Mutability**: Modify dictionaries after creation (add/update/delete entries).  
2. **Dynamic Views**: `keys()` and `values()` provide live updates.  
3. **Key Restrictions**: Keys must be hashable (immutable).  
4. **Efficiency**: Fast lookups using keys (O(1) complexity).  
5. **Use Cases**:  
   - Structured data (e.g., user profiles, configurations).  
   - Frequency counting (e.g., word occurrences).  
   - Grouping related data.  