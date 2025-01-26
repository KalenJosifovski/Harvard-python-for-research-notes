---
Video path: 
Subtitle path: 
tags:
  - python-modules
  - namespaces
  - methods
  - imports
---

# Summary

## 1. **Importing Modules**  
   - **Description**: Use `import` to access external code libraries.  
   - **Syntax**:  
     - Full module: `import module_name`  
     - Specific object: `from module import object`  
   - **Examples**:  
     ```python  
     # Import entire math module  
     import math  
     print(math.pi)          # Output: 3.141592653589793  

     # Import only pi from math  
     from math import pi  
     print(pi)               # Output: 3.141592653589793  

     # Alias imports (e.g., numpy)  
     import numpy as np  
     ```

## 2. **Module Namespaces**  
   - **Description**: Modules have isolated namespaces to prevent naming conflicts.  
   - **Example** (math vs. numpy functions):  
     ```python  
     import math, numpy as np  

     # math.sqrt (single value)  
     print(math.sqrt(2))     # Output: 1.4142135623730951  

     # np.sqrt (supports arrays)  
     print(np.sqrt([2, 3, 4]))  # Output: [1.4142 1.7320 2.0]  
     ```

## 3. **How Imports Work**  
   - **Process**:  
     1. Creates a new namespace for the module.  
     2. Executes the module’s code in that namespace.  
     3. Binds the namespace to a name (e.g., `np` for numpy).  
   - **Example**:  
     ```python  
     import numpy as np  # Namespace "np" now references numpy's functions  
     ```

## 4. **Inspecting Objects**  
   - **Type Checking**: Use `type()` to identify an object’s class.  
   - **Method Discovery**: Use `dir()` to list available methods.  
   - **Examples**:  
     ```python  
     name = "Amy"  

     # Check type  
     print(type(name))       # Output: <class 'str'>  

     # List methods via instance or class  
     print(dir(name))        # Lists all string methods  
     print(dir(str))         # Same as above  
     ```

## 5. **Using the `help()` Function**  
   - **Description**: Get brief documentation for methods (avoid invoking them).  
   - **Example**:  
     ```python  
     # Correct usage (no parentheses)  
     help(str.upper)         # Displays help for the upper() method  

     # Incorrect usage (accidentally calls the method)  
     # help(name.upper())    # Throws an error  
     ```

## 6. **Module Functions vs. Methods**  
   - **Functions**: Standalone (e.g., `math.sqrt()`).  
   - **Methods**: Attached to objects (e.g., `str.upper()`).  
   - **Example**:  
     ```python  
     # Module function  
     import math  
     print(math.sin(math.pi/2))  # Output: 1.0  

     # Object method  
     text = "hello"  
     print(text.upper())         # Output: "HELLO"  
     ```

---

### Key Takeaways:  
1. **Namespaces** prevent conflicts (e.g., `math.sqrt` vs. `np.sqrt`).  
2. Use `dir()` and `help()` to explore methods without guessing.  
3. **Import selectively** (`from math import pi`) to reduce clutter.  
4. **Module functions** operate independently; **methods** depend on object state.  