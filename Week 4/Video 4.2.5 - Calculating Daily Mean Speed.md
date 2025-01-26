---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [time-series, pandas, data-aggregation]  
---

# Summary

## 1. **Algorithm for Daily Mean Speed Calculation**  
   - **Objective**: Group observations by day and compute mean speed for each day.  
   - **Steps**:  
     1. **Initialize Variables**:  
        ```python  
        next_day = 1  
        inds = []  
        daily_mean_speed = []  
        ```  
     2. **Loop Through Observations**:  
        ```python  
        for i, t in enumerate(elapsed_days):  # elapsed_days = days since first observation  
            if t < next_day:  
                inds.append(i)  
            else:  
                # Compute mean speed for collected indices  
                if inds:  # Skip if no data for the day  
                    mean_speed = np.mean(bird_data['speed_2D'].iloc[inds])  
                    daily_mean_speed.append(mean_speed)  
                # Reset for next day  
                next_day += 1  
                inds = [i]  
        # Handle last day  
        if inds:  
            daily_mean_speed.append(np.mean(bird_data['speed_2D'].iloc[inds]))  
        ```  

## 2. **Plotting Daily Mean Speed**  
   - **Syntax**:  
     ```python  
     import matplotlib.pyplot as plt  
     days = range(len(daily_mean_speed))  
     plt.plot(days, daily_mean_speed, 'b-')  
     plt.xlabel("Days Since First Observation")  
     plt.ylabel("Mean Daily Speed (m/s)")  
     plt.title("Eric's Daily Mean Flight Speed")  
     plt.savefig("daily_speed_plot.pdf")  
     plt.show()  
     ```  
   - **Key Features**:  
     - Identifies migration periods (e.g., peaks at ~90 and ~230 days).  
     - Highlights irregular sampling intervals.  

## 3. **Edge Case Handling**  
   - **Empty Days**: Skip days with no observations using `if inds:`.  
   - **Data Validation**:  
     ```python  
     # Ensure elapsed_days is integer type  
     elapsed_days = [int(t) for t in elapsed_days]  
     ```  

---

### Key Takeaways:  
1. **Grouping Logic**:  
   - Use `next_day` to track day transitions and `inds` to accumulate indices.  
   - Reset indices and increment `next_day` upon encountering a new day.  
2. **Migration Detection**:  
   - Peaks in daily mean speed indicate migration events (e.g., ~9 m/s at day 90).  
3. **Robustness**:  
   - Handle empty days to avoid `NaN` values or errors.  
4. **Applications**:  
   - Track behavioral patterns (e.g., migration, foraging) in GPS data.  
   - Monitor sensor data trends over time.  