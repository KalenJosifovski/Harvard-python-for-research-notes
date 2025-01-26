---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-statements, compound-statements, control-flow]  
---

# Summary

## 1. **Basic Statement Types**  
   - **`return`**: Exits a function and returns a value.  
   - **`import`**: Loads modules/packages into the program.  
   - **`pass`**: Placeholder for empty code blocks (no operation).  
   - **Examples**:  
     ```python  
     def example():  
         pass  # Placeholder for future code  

     import math  # Import math module  
     ```

## 2. **Compound Statements**  
   - **Structure**:  
     - **Header**: Starts with a keyword (e.g., `if`, `for`) and ends with `:`.  
     - **Block/Suite**: Indented group of statements under the header.  
   - **Indentation Rules**:  
     - Mandatory in Python (defines code grouping).  
     - Use consistent indentation (spaces/tabs).  

## 3. **If-Elif-Else Statements**  
   - **Syntax**: Executes code blocks based on conditions.  
   - **Example (Absolute Value Calculation)**:  
     ```python  
     x = 5  
     y = 3  
     if x > y:  
         absval = x - y  
     elif y > x:  
         absval = y - x  
     else:  
         absval = 0  
     print(absval)  # Output: 2  
     ```  

## 4. **Execution Flow**  
   - **Order**: Checks `if` → `elif` (if any) → `else` (if all fail).  
   - **Short-Circuiting**: Stops at the first true condition.  

---

### Key Takeaways:  
1. **Indentation Matters**: Defines code blocks (unlike many other languages).  
2. **Compound Statements**: Use headers (`if`, `for`, etc.) and indented blocks.  
3. **Common Use Cases**:  
   - `if-elif-else`: Multi-condition decision-making.  
   - `pass`: Temporarily skip unimplemented code.  
4. **Built-in Functions**: Prefer `abs()` for absolute values (example used for illustration).  