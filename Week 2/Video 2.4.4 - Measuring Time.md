---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-timing, performance, optimization]  
---

# Summary

## 1. **Measuring Execution Time**  
   - **Syntax**: Use `time.clock()` (Python 2) or `time.perf_counter()` (Python 3) to capture start/end times.  
   - **Description**: Calculates CPU time (processor time) for code blocks to compare performance.  
   - **Example**:  
     ```python  
     import time  

     # Start timer  
     start_time = time.perf_counter()  

     # Code to measure  
     total = sum(range(1_000_000))  

     # End timer  
     end_time = time.perf_counter()  

     print(f"Time elapsed: {end_time - start_time:.4f} seconds")  
     ```

## 2. **Comparing Python vs. NumPy Performance**  
   - **Syntax**: Time pure Python loops vs. vectorized NumPy operations.  
   - **Description**: NumPy’s vectorization drastically reduces execution time.  
   - **Example**:  
     ```python  
     # Pure Python implementation  
     start_py = time.perf_counter()  
     rolls = [random.choice(range(1, 7)) for _ in range(1_000_000)]  
     end_py = time.perf_counter()  

     # NumPy implementation  
     start_np = time.perf_counter()  
     rolls_np = np.random.randint(1, 7, 1_000_000)  
     end_np = time.perf_counter()  

     print(f"Python: {end_py - start_py:.2f}s | NumPy: {end_np - start_np:.2f}s")  
     # Example Output: Python: 1.23s | NumPy: 0.02s (60x faster)  
     ```

## 3. **Extrapolating Runtime**  
   - **Syntax**: Time smaller datasets to estimate larger runs.  
   - **Description**: Use linear scaling or complexity analysis to predict execution time for big data.  
   - **Example**:  
     ```python  
     small_data_time = 0.5  # Time for 10,000 samples  
     estimated_large_data_time = small_data_time * (1_000_000 / 10_000)  # ~50 seconds  
     ```

---

### Key Takeaways:  
1. **Timing Tools**:  
   - Prefer `time.perf_counter()` (Python 3) over deprecated `time.clock()`.  
   - Use `%%time` in Jupyter notebooks for quick measurements.  
2. **NumPy Efficiency**:  
   - Vectorized operations (e.g., `np.random.randint`) are **10-100x faster** than Python loops.  
3. **Benchmarking**:  
   - Test multiple implementations to identify bottlenecks.  
   - Profile code with tools like `cProfile` for detailed insights.  
4. **Scaling Predictions**:  
   - Measure small-scale performance to estimate large-scale runtime.  
