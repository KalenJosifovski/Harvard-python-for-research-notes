---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [cartopy, geospatial, data-visualization]  
---

# Summary

## 1. **Installing Cartopy**  
   - **Syntax (Anaconda)**:  
     ```bash  
     conda install -c conda-forge cartopy  
     ```  
   - **Description**:  
     - Cartopy is a Python library for geospatial data visualization.  
     - Use Anaconda for hassle-free installation across platforms (Mac/Windows).  

## 2. **Basic Map Setup**  
   - **Syntax**:  
     ```python  
     import cartopy.crs as ccrs  
     import matplotlib.pyplot as plt  
     # Initialize map with projection (e.g., PlateCarree)  
     fig = plt.figure(figsize=(10, 6))  
     ax = plt.axes(projection=ccrs.PlateCarree())  
     ```  
   - **Key Parameters**:  
     - `ccrs.PlateCarree()`: A common projection for latitude/longitude data.  

## 3. **Plotting Bird Trajectories**  
   - **Syntax**:  
     ```python  
     bird_names = birddata.bird_name.unique()  
     for name in bird_names:  
         ix = birddata.bird_name == name  
         x = birddata.longitude[ix]  
         y = birddata.latitude[ix]  
         ax.plot(x, y, ".", markersize=1, transform=ccrs.PlateCarree(), label=name)  
     ```  
   - **Description**:  
     - `transform=ccrs.PlateCarree()` ensures coordinates align with the chosen projection.  

## 4. **Adding Geographic Features**  
   - **Syntax**:  
     ```python  
     ax.add_feature(cartopy.feature.LAND)  
     ax.add_feature(cartopy.feature.OCEAN)  
     ax.add_feature(cartopy.feature.COASTLINE)  
     ax.add_feature(cartopy.feature.BORDERS, linestyle=':')  
     ax.set_extent([-25, 20, 35, 60])  # Adjust to focus on Europe  
     ```  
   - **Features**:  
     - Overlay land, ocean, coastlines, and country borders for context.  

## 5. **Final Visualization**  
   - **Syntax**:  
     ```python  
     plt.legend(loc="lower right")  
     plt.savefig("bird_migration_map.pdf")  
     ```  
   - **Output**:  
     - A map with bird trajectories overlaid on geographic features.  
     - Example: Nico and Sanne’s paths extending further south than Eric’s.  

---

### Key Takeaways:  
1. **Cartopy Advantages**:  
   - Accurate spatial representation vs. distorted 2D plots.  
   - Easy integration with `matplotlib` for geospatial visualizations.  
2. **Workflow**:  
   - Install → Set projection → Plot data → Add map features → Customize.  
3. **Practical Use**:  
   - Reveals migration routes in geographic context (e.g., coastal vs. inland paths).  
4. **Customization**:  
   - Adjust `set_extent()` to focus on specific regions (e.g., Europe for this dataset).  