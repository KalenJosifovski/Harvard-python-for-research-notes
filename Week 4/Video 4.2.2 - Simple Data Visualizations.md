---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [gps-tracking, matplotlib, data-visualization]  
---

# Summary

## 1. **Plotting a Single Bird's Trajectory**  
   - **Syntax**:  
     ```python  
     import matplotlib.pyplot as plt  
     # Extract Eric's data  
     ix = birddata.bird_name == "Eric"  
     x = birddata.longitude[ix]  
     y = birddata.latitude[ix]  
     # Plot  
     plt.figure(figsize=(10, 6))  
     plt.plot(x, y, "b.", markersize=1, label="Eric")  
     plt.xlabel("Longitude")  
     plt.ylabel("Latitude")  
     plt.legend(loc="lower right")  
     plt.savefig("eric_trajectory.pdf")  
     ```  
   - **Output**:  
     - A 2D scatter plot showing Eric’s flight path (longitude vs. latitude).  
     - Distortion noted due to projecting spherical coordinates onto a flat plane.  

## 2. **Visualizing All Three Birds**  
   - **Syntax**:  
     ```python  
     bird_names = birddata.bird_name.unique()  
     plt.figure(figsize=(10, 6))  
     for name in bird_names:  
         ix = birddata.bird_name == name  
         x = birddata.longitude[ix]  
         y = birddata.latitude[ix]  
         plt.plot(x, y, ".", markersize=1, label=name)  
     plt.xlabel("Longitude")  
     plt.ylabel("Latitude")  
     plt.legend(loc="lower right")  
     plt.savefig("all_birds_trajectories.pdf")  
     ```  
   - **Key Observations**:  
     - All three birds (Eric, Nico, Sanne) follow broadly similar migration routes.  
     - Nico and Sanne travel further south compared to Eric.  

## 3. **Limitations of 2D Projection**  
   - **Note**:  
     - Latitude/longitude plots on a Cartesian plane introduce distortion over large distances.  
     - Acknowledged as a simplification for initial exploratory analysis.  

---

### Key Takeaways:  
1. **Quick Visualization**:  
   - Use `matplotlib` to plot GPS coordinates for rapid insights despite geometric distortions.  
2. **Comparative Analysis**:  
   - Overlaying multiple trajectories reveals behavioral differences (e.g., migration range).  
3. **Code Reusability**:  
   - Loop through unique bird names to automate plotting for multiple subjects.  
4. **Next Steps**:  
   - Implement cartographic projections (e.g., Mercator) for accurate spatial representation.  