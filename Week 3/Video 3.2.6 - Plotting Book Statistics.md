---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [data-visualization, matplotlib, pandas]  
---

# Summary

## 1. **Extracting DataFrame Columns**  
   - **Syntax**:  
     ```python  
     # Access "length" and "unique" columns  
     x = stats.length  
     y = stats.unique  
     ```  
   - **Description**:  
     - Use pandas column names (`stats.length`, `stats.unique`) to extract data for plotting.  

## 2. **Basic Scatter Plot**  
   - **Syntax**:  
     ```python  
     import matplotlib.pyplot as plt  
     plt.plot(stats.length, stats.unique, "bo")  # "bo" = blue circles  
     plt.xlabel("Book Length (total words)")  
     plt.ylabel("Unique Words")  
     plt.show()  
     ```  
   - **Description**:  
     - Plot book length vs. unique words using `plt.plot()`.  

## 3. **Log-Log Plot**  
   - **Syntax**:  
     ```python  
     plt.loglog(stats.length, stats.unique, "bo")  
     plt.xlabel("Book Length (log scale)")  
     plt.ylabel("Unique Words (log scale)")  
     plt.show()  
     ```  
   - **Description**:  
     - Visualize logarithmic relationships to identify linear trends in data.  

## 4. **Stratifying Data by Language**  
   - **Syntax**:  
     ```python  
     # Create subsets for each language  
     english = stats[stats.language == "English"]  
     french = stats[stats.language == "French"]  
     # Repeat for German, Portuguese, etc.  
     ```  
   - **Example**:  
     ```python  
     plt.loglog(english.length, english.unique, "o", color="crimson", label="English")  
     plt.loglog(french.length, french.unique, "o", color="forestgreen", label="French")  
     ```  

## 5. **Multi-Language Plot with Custom Colors**  
   - **Syntax**:  
     ```python  
     plt.figure(figsize=(10, 10))  # Set plot size  
     # English (crimson)  
     plt.loglog(english.length, english.unique, "o", color="crimson", label="English")  
     # French (forestgreen)  
     plt.loglog(french.length, french.unique, "o", color="forestgreen", label="French")  
     # German (orange)  
     plt.loglog(german.length, german.unique, "o", color="orange", label="German")  
     # Portuguese (blueviolet)  
     plt.loglog(portuguese.length, portuguese.unique, "o", color="blueviolet", label="Portuguese")  

     plt.legend()  
     plt.xlabel("Book Length")  
     plt.ylabel("Unique Words")  
     plt.savefig("lang_plot.pdf")  # Save as PDF  
     ```  
   - **Description**:  
     - Use HTML color names for styling.  
     - Add labels and legends for clarity.  

---

### Key Takeaways:  
1. **Log-Log Scaling**:  
   - Reveals linear trends in data with wide-ranging values (e.g., word counts from 1k to 1M).  
2. **Data Stratification**:  
   - Compare language-specific patterns using boolean indexing (`stats[stats.language == "English"]`).  
3. **Visual Customization**:  
   - Customize markers, colors, and labels to enhance plot readability.  
4. **Exporting Plots**:  
   - Use `plt.savefig()` to save visualizations for reports or further analysis.  