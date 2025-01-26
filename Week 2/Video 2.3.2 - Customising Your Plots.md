---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [matplotlib, plot-customization, visualization]  
---

# Summary

## 1. **Adding Legends**  
   - **Syntax**: Assign `label` to plots and call `plt.legend()`. Use `loc` to specify legend position.  
   - **Description**: Labels differentiate datasets; legends make plots interpretable.  
   - **Example**:  
     ```python  
     plt.plot(x, y1, label="First Dataset")  
     plt.plot(x, y2, label="Second Dataset")  
     plt.legend(loc="upper left")  # Positions legend in top-left corner  
     plt.show()  
     ```

## 2. **Adjusting Axes**  
   - **Syntax**: `plt.axis([xmin, xmax, ymin, ymax])`  
   - **Description**: Sets explicit axis limits to control plot boundaries.  
   - **Example**:  
     ```python  
     plt.axis([-0.5, 10.5, -5, 105])  # Expands axis beyond data range  
     plt.show()  
     ```

## 3. **Axis Labels with LaTeX**  
   - **Syntax**: Use `plt.xlabel()`/`plt.ylabel()` with LaTeX syntax inside `$...$`.  
   - **Description**: Enables mathematical notation in labels (e.g., `$y = x^2$`).  
   - **Examples**:  
     ```python  
     plt.xlabel("$x$ (units)")  # LaTeX-formatted label  
     plt.ylabel("$y$ (units)")  
     # Without LaTeX:  
     plt.xlabel("X Axis")  
     plt.ylabel("Y Axis")  
     ```

## 4. **Saving Figures**  
   - **Syntax**: `plt.savefig("filename.ext")` (supports PDF, PNG, SVG, etc.).  
   - **Description**: Saves plots to files for sharing or publication.  
   - **Example**:  
     ```python  
     plt.savefig("myplot.pdf")  # Saves as PDF  
     plt.savefig("myplot.png", dpi=300)  # High-resolution PNG  
     ```

---

### Key Takeaways:  
1. **Legends**: Always label datasets and use `plt.legend()` for clarity.  
2. **Axis Control**:  
   - Use `plt.axis()` to adjust plot boundaries.  
   - LaTeX enhances labels for technical plots.  
3. **Saving Plots**:  
   - Choose formats like PDF for vector graphics or PNG for raster images.  
   - Adjust `dpi` (dots per inch) for image quality.  
4. **Workflow**: Customize plots incrementally (labels → axes → legend → save).  