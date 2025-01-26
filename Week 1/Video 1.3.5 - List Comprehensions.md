---
Video path: 
Subtitle path: 
tags:
---
# Summary

## 1. **Basic List Comprehension**
   - **Description**: A concise way to create a new list by applying an operation to each item in an existing list. Combines a `for` loop and an expression into a single line.
   - **Syntax**: `[expression for item in iterable]`
   - **Example**:
     ```python
     # Traditional approach using a for loop
     numbers = [1, 2, 3, 4]
     squares = []
     for number in numbers:
         square = number ** 2
         squares.append(square)
     print(squares)  # Output: [1, 4, 9, 16]

     # Equivalent list comprehension
     squares2 = [number ** 2 for number in numbers]
     print(squares2)  # Output: [1, 4, 9, 16]
     ```

## 2. **Advantages of List Comprehensions**
   - **Speed**: List comprehensions are optimised and often faster than equivalent loops with `append()`.
   - **Elegance**: Achieve the same result in fewer lines, improving readability and reducing boilerplate code.
   - **Example Use Case**:
     ```python
     # Convert strings to uppercase
     words = ["hello", "world", "python"]
     upper_words = [word.upper() for word in words]
     print(upper_words)  # Output: ['HELLO', 'WORLD', 'PYTHON']
     ```

## 3. **Structure of a List Comprehension**
   - **Components**:
     1. **Expression**: The operation applied to each item (e.g., `number ** 2`).
     2. **Iteration**: A `for` loop to iterate over the original list (e.g., `for number in numbers`).
   - **Example**:
     ```python
     # Filter even numbers and square them
     numbers = [1, 2, 3, 4, 5]
     even_squares = [num ** 2 for num in numbers if num % 2 == 0]
     print(even_squares)  # Output: [4, 16]
     ```  

---

### Key Takeaways:  
1. **Conciseness**: List comprehensions replace multi-line loops with a single line, making code cleaner and more Pythonic.  
2. **Efficiency**: They are faster than traditional loops due to internal optimizations.  
3. **Flexibility**: Support filtering (e.g., `if num % 2 == 0`) and complex expressions, enabling powerful transformations in minimal code.  
4. **Readability**: Simplify code structure while maintaining clarity, especially for straightforward data transformations.