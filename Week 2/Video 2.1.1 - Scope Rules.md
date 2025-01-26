---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-scope, LEGB-rule, variable-mutability]  
---

# Summary

## 1. **LEGB Scope Rules**  
   - **Syntax**: Python resolves variable names in the order: **Local → Enclosing → Global → Built-in**.  
   - **Description**: Determines which variable/function is used based on its scope hierarchy.  
   - **Example**:  
     ```python  
     x = "global"  
     def func():  
         x = "local"  
         print(x)  # Output: "local" (Local scope takes precedence)  
     func()  
     ```

## 2. **Modifying Global Variables**  
   - **Syntax**: Use `global` to modify immutable global variables; mutable objects (e.g., lists) can be modified directly.  
   - **Description**: Changes to mutable global objects persist without `global`.  
   - **Example**:  
     ```python  
     x = [1, 2]  
     def modify_list():  
         x.append(3)  # Modifies global list without `global` keyword  
     modify_list()  
     print(x)  # Output: [1, 2, 3]  
     ```

## 3. **Side Effects in Functions**  
   - **Syntax**: Functions altering variables outside their scope create side effects.  
   - **Description**: Avoid unintended changes to global state for cleaner code.  
   - **Example**:  
     ```python  
     y = 10  
     def risky_func():  
         global y  
         y += 5  # Modifies global variable (side effect)  
     risky_func()  
     print(y)  # Output: 15  
     ```

## 4. **Local vs. Global Variable Assignment**  
   - **Syntax**: Assigning a variable inside a function creates a local copy, even if a global variable with the same name exists.  
   - **Description**: Use `global` to override this behavior for immutable types.  
   - **Example**:  
     ```python  
     z = 100  
     def reassign():  
         z = 200  # Creates a local variable, not modifying global z  
     reassign()  
     print(z)  # Output: 100 (global z unchanged)  
     ```

## 5. **Mutability and Scope**  
   - **Syntax**: Mutable objects (e.g., lists) passed to functions can be modified in-place.  
   - **Description**: Changes to mutable arguments affect the original object.  
   - **Example**:  
     ```python  
     def update_list(lst):  
         lst.append(99)  # Modifies the original list  
     my_list = [1, 2]  
     update_list(my_list)  
     print(my_list)  # Output: [1, 2, 99]  
     ```

---

### Key Takeaways:  
1. **Scope Hierarchy**: Follow the LEGB rule to resolve variable names.  
2. **Global Modifications**:  
   - Use `global` for immutable types (e.g., integers).  
   - Mutable objects (e.g., lists) can be modified directly.  
3. **Avoid Side Effects**: Minimize unintended changes to global variables.  
4. **Local Variables**: Assignments inside functions default to local scope unless declared `global`.  
5. **Mutability**: Passing mutable objects to functions allows in-place modifications, affecting the original object.  