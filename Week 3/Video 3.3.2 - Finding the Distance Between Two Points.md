---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [mathematics, numpy, geometry]  
---

# Summary

## 1. **Euclidean Distance Formula**  
   - **Formula**:  
     $$ d = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2} $$  
   - **Description**:  
     - Derived from the Pythagorean theorem.  
     - Measures straight-line distance between two points in 2D space.  

## 2. **Distance Calculation with NumPy**  
   - **Syntax**:  
     ```python  
     import numpy as np  
     p1 = np.array([1, 1])  # Point 1: (x1, y1)  
     p2 = np.array([4, 4])  # Point 2: (x2, y2)  
     diff = p2 - p1  
     squared_diff = np.power(diff, 2)  
     distance = np.sqrt(np.sum(squared_diff))  
     ```  
   - **Example Output**:  
     ```python  
     print(distance)  # 4.2426 (≈√18)  
     ```  

## 3. **Reusable Distance Function**  
   - **Syntax**:  
     ```python  
     def distance(p1, p2):  
         """  
         Computes Euclidean distance between two points.  
         Args:  
             p1 (np.array): Coordinates of first point.  
             p2 (np.array): Coordinates of second point.  
         Returns:  
             float: Euclidean distance.  
         """  
         return np.sqrt(np.sum(np.power(p2 - p1, 2)))  
     ```  
   - **Usage**:  
     ```python  
     point_a = np.array([2, 3])  
     point_b = np.array([5, 7])  
     print(distance(point_a, point_b))  # 5.0  
     ```  

## 4. **Vectorized Operations**  
   - **Syntax**:  
     ```python  
     # Calculate distance for multiple point pairs  
     points1 = np.array([[1, 1], [2, 3], [0, 0]])  
     points2 = np.array([[4, 4], [5, 7], [3, 4]])  
     distances = np.sqrt(np.sum(np.power(points2 - points1, 2), axis=1))  
     ```  
   - **Output**:  
     ```python  
     print(distances)  # [4.2426, 5.0, 5.0]  
     ```  

---

### Key Takeaways:  
1. **Formula Foundation**:  
   - Euclidean distance relies on squaring coordinate differences and summing them.  
2. **NumPy Efficiency**:  
   - Use vectorized NumPy operations for fast computations on arrays of points.  
3. **Function Design**:  
   - Encapsulate logic in reusable functions for clean and maintainable code.  
4. **Generalization**:  
   - Extends naturally to 3D or higher dimensions by adding terms (e.g., $(z_2 - z_1)^2$).  