---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [datetime, pandas, time-series]  
---

# Summary

## 1. **Converting String Timestamps to Datetime Objects**  
   - **Syntax**: Use `datetime.strptime()` with format specifiers.  
   - **Example**:  
     ```python  
     from datetime import datetime  
     # Sample timestamp string: "2013-08-15T00:18:25+00"  
     date_str = bird_data['date_time'][0][:-3]  # Remove UTC offset (+00)  
     dt_obj = datetime.strptime(date_str, "%Y-%m-%dT%H:%M:%S")  
     ```  
   - **Key Format Specifiers**:  
     - `%Y`: 4-digit year  
     - `%m`: 2-digit month  
     - `%d`: 2-digit day  
     - `%H`: 24-hour format hour  

## 2. **Adding Datetime Column to DataFrame**  
   - **Steps**:  
     1. Convert all timestamp strings to datetime objects.  
     2. Create a pandas Series and append to DataFrame.  
   - **Code**:  
     ```python  
     import pandas as pd  
     timestamps = []  
     for k in range(len(bird_data)):  
         date_str = bird_data['date_time'][k][:-3]  
         dt = datetime.strptime(date_str, "%Y-%m-%dT%H:%M:%S")  
         timestamps.append(dt)  
     # Add as new column  
     bird_data['timestamp'] = pd.Series(timestamps, index=bird_data.index)  
     ```

## 3. **Calculating Time Intervals**  
   - **Syntax**: Subtract datetime objects to get `timedelta`.  
   - **Example**:  
     ```python  
     # Time elapsed since first observation (in days)  
     times = bird_data['timestamp']  
     elapsed_days = [(t - times[0]).days for t in times]  
     # Convert to hours  
     elapsed_hours = [(t - times[0]).total_seconds() / 3600 for t in times]  
     ```

## 4. **Visualizing Temporal Data**  
   - **Plotting Elapsed Time**:  
     ```python  
     import matplotlib.pyplot as plt  
     plt.plot(bird_data.index, elapsed_days, 'b-')  
     plt.xlabel("Observation Index")  
     plt.ylabel("Days Since First Observation")  
     plt.title("Elapsed Time for Eric's GPS Data")  
     plt.savefig("timeplot.pdf")  
     plt.show()  
     ```  
   - **Insight**: Gaps/jumps in the plot indicate irregular sampling intervals.  

---

### Key Takeaways:  
1. **Datetime Conversion**:  
   - Always strip irrelevant parts (e.g., UTC offsets) before parsing.  
   - Use `strptime` with precise format strings for reliable parsing.  
2. **Time Arithmetic**:  
   - `timedelta` objects enable calculations in units like days (`.days`) or seconds (`.total_seconds()`).  
3. **Data Consistency**:  
   - Visualizing elapsed time helps identify irregular sampling intervals.  
4. **Pandas Integration**:  
   - Store datetime objects in DataFrames for seamless time-series operations.  
5. **Applications**:  
   - Critical for analyzing temporal patterns in GPS tracking, sensor data, or event logs.  