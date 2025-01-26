---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-file-io, data-cleaning, bioinformatics]  
---

# Summary

## 1. **Setting the Working Directory**  
   - **Syntax**: Use terminal commands (`pwd`, `cd`) or IDE tools to navigate to the directory containing `dna.txt`.  
   - **Description**: Ensure Python’s working directory matches the file location to avoid `FileNotFoundError`.  

## 2. **Reading the DNA File**  
   - **Syntax**:  
     ```python  
     input_file = "dna.txt"  
     with open(input_file, "r") as f:  
         seq = f.read()  
     ```  
   - **Description**:  
     - `open()` opens the file in read mode (`"r"`).  
     - `f.read()` loads the entire file content into the variable `seq`.  

## 3. **Cleaning the Data**  
   - **Syntax**: Remove newline (`\n`) and carriage return (`\r`) characters.  
   - **Example**:  
     ```python  
     # Remove line breaks  
     seq = seq.replace("\n", "")  
     # Remove carriage returns (if present)  
     seq = seq.replace("\r", "")  
     ```  
   - **Note**: Strings are immutable in Python; `replace()` returns a new string.  

## 4. **Validating the Cleaned Sequence**  
   - **Syntax**: Use `print()` to inspect the cleaned sequence.  
   - **Example**:  
     ```python  
     print(seq[:100])  # Print first 100 characters  
     ```  

---

### Key Takeaways:  
1. **File Handling**:  
   - Use `with open(...)` for automatic file closure (safer than manual `f.close()`).  
2. **Data Cleaning**:  
   - Remove `\n` and `\r` to avoid translation errors.  
3. **Immutability**:  
   - Always reassign the cleaned string (e.g., `seq = seq.replace(...)`).  
4. **Verification**:  
   - Print portions of the sequence to confirm cleanliness and integrity.  