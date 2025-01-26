---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-files, file-io, read-write]  
---

# Summary

## 1. **Reading Files**  
   - **Syntax**: Use `open(filename)` with a `for` loop to iterate line-by-line.  
   - **Line Breaks**: Lines include `\n` (newline character); use `.rstrip()` to remove it.  
   - **Example**:  
     ```python  
     # Read and print lines from a file  
     for line in open("input.txt"):  
         print(line.rstrip())  # Remove trailing newline  
     ```

## 2. **Processing Lines**  
   - **Splitting Lines**: Use `.split()` to break lines into lists (default splits on whitespace).  
   - **Example**:  
     ```python  
     # Split lines into words  
     for line in open("input.txt"):  
         words = line.rstrip().split()  
         print(words)  # Output: ["first"], ["second"], ["third"]  
     ```

## 3. **Writing Files**  
   - **Open for Writing**: Use `open(filename, "w")` to create/overwrite a file.  
   - **Write Lines**: Use `.write()`; add `\n` manually for line breaks.  
   - **Close File**: Always close the file with `.close()` to save changes.  
   - **Example**:  
     ```python  
     # Write to a file  
     f = open("output.txt", "w")  
     f.write("Python\n")  # Include \n for line breaks  
     f.close()  
     ```

---

### Key Takeaways:  
1. **Reading Files**:  
   - Loop directly over `open(filename)` to read lines.  
   - Strip newlines with `.rstrip()` for clean processing.  
2. **Writing Files**:  
   - Use mode `"w"` to write (overwrites existing content; use `"a"` to append).  
   - Explicitly add `\n` to create line breaks.  
3. **File Closure**: Always close files after writing to ensure data is saved.  
4. **Best Practice**: Consider using `with` statements for automatic closure:  
   ```python  
   with open("output.txt", "w") as f:  
       f.write("Python\n")  # No need to call f.close()  