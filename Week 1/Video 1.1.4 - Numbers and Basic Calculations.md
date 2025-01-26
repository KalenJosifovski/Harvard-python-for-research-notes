---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-numbers, arithmetic, math-module, operators]  
---

# Summary

## 1. **Numeric Types in Python**  
   - **Integers (`int`)**: Unlimited precision (e.g., `10**100`).  
   - **Floats (`float`)**: Represent decimals (e.g., `3.14`).  
   - **Complex (`complex`)**: Written as `a + bj` (e.g., `3+4j`).  
   - **Example**:  
     ```python  
     large_int = 10**100  # Valid integer  
     float_num = 5 + 3.0  # Result: 8.0 (float)  
     complex_num = (3+4j) * 2  # Result: 6+8j  
     ```

## 2. **Arithmetic Operations**  
   - **Basic Operators**: `+`, `-`, `*`, `/`, `**` (exponent).  
   - **Floor Division**: `//` truncates decimals (rounds down).  
   - **Modulo**: `%` returns remainder.  
   - **Examples**:  
     ```python  
     print(15 / 7)   # Output: 2.142857... (float)  
     print(15 // 7)  # Output: 2 (int)  
     print(7 % 3)    # Output: 1  
     print(2 ** 10)  # Output: 1024  
     ```

## 3. **Underscore `_` in Interactive Mode**  
   - **Description**: `_` stores the last result in interactive sessions.  
   - **Example**:  
     ```python  
     >>> 15 / 2.3  
     6.521739130434782  
     >>> _ * 2.3  # Uses previous result  
     15.0  
     ```

## 4. **Math Module Functions**  
   - **Usage**: Import `math` for advanced operations (e.g., factorial, sqrt).  
   - **Example**:  
     ```python  
     import math  
     print(math.factorial(3))  # Output: 6  
     print(math.sqrt(25))      # Output: 5.0  
     ```

## 5. **Type Mixing and Conversions**  
   - **Implicit Conversion**: Operations with mixed types return floats.  
   - **Explicit Conversion**: Use `int()`, `float()`, `complex()`.  
   - **Example**:  
     ```python  
     result = 5 + 3.0      # Output: 8.0 (float)  
     converted = int(8.9)  # Output: 8 (truncates, does not round)  
     ```

## 6. **Complex Number Operations**  
   - **Syntax**: Use `j` for imaginary units.  
   - **Example**:  
     ```python  
     c1 = 3 + 4j  
     c2 = 2 - 1j  
     print(c1 + c2)  # Output: (5+3j)  
     print(c1.real)  # Output: 3.0  
     ```

---

### Key Takeaways:  
1. **Unlimited precision** for integers avoids overflow errors.  
2. Floor division (`//`) truncates decimals; regular division (`/`) returns floats.  
3. Use `math` module for advanced functions (e.g., `factorial`, `sqrt`).  
4. `_` in interactive mode simplifies sequential calculations.  
5. Mixing numeric types implicitly converts results to the "wider" type (e.g., `int + float → float`).  