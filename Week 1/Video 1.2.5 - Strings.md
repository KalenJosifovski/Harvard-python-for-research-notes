---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-strings, immutability, methods, polymorphism]  
---

# Summary

## 1. **String Basics**  
   - **Immutable Sequences**: Strings cannot be modified after creation.  
   - **Syntax**: Enclosed in `' '`, `" "`, or `''' '''`.  
   - **Indexing/Slicing**: Use zero-based indexing and slicing.  
   - **Example**:  
     ```python  
     s = "Python"  
     print(s[0])       # Output: 'P'  
     print(s[-3:])     # Output: 'hon' (last 3 characters)  
     print(len(s))     # Output: 6  
     ```

## 2. **String Operations**  
   - **Concatenation (`+`)**: Combine strings.  
   - **Repetition (`*`)**: Repeat strings multiple times.  
   - **Membership (`in`)**: Check if a substring exists.  
   - **Examples**:  
     ```python  
     print("Hello" + " " + "World")  # Output: "Hello World"  
     print("Na" * 2 + " Batman!")     # Output: "NaNa Batman!"  
     print("y" in "Python")           # Output: True  
     ```

## 3. **Type Handling & Polymorphism**  
   - **Operator Behavior**: `+` and `*` depend on data types.  
   - **Explicit Conversion**: Use `str()` to mix types.  
   - **Example**:  
     ```python  
     # Error: "Value: " + 8 → TypeError  
     corrected = "Value: " + str(8)  # Output: "Value: 8"  
     ```

## 4. **String Methods**  
   - **`.replace()`**: Replace substrings (returns a new string).  
   - **`.split()`**: Split into a list of substrings.  
   - **Case Methods**: `.upper()`, `.lower()`, etc.  
   - **Examples**:  
     ```python  
     name = "Tina Fey"  
     new_name = name.replace("T", "t")  # Output: "tina Fey"  
     parts = name.split(" ")            # Output: ["Tina", "Fey"]  
     print(parts[0].upper())            # Output: "TINA"  
     ```

## 5. **Immutability in Action**  
   - **Behavior**: Methods return new strings; original remains unchanged.  
   - **Example**:  
     ```python  
     original = "Hello"  
     modified = original.replace("H", "J")  
     print(original)  # Output: "Hello"  
     print(modified)  # Output: "Jello"  
     ```

---

### Key Takeaways:  
1. **Immutability**: All string operations return new objects.  
2. **Polymorphism**: Operators (`+`, `*`) adapt to string context.  
3. **Method Chaining**: Combine methods like `split()` and `upper()` for transformations.  
4. **Explicit Conversion**: Use `str()` to concatenate strings with non-strings.  
5. **Common Methods**:  
   - `replace()`: Substitution.  
   - `split()`: Break into parts.  
   - `upper()/lower()`: Case manipulation.  