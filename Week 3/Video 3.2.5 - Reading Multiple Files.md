---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-file-io, data-organization, pandas]  
---

# Summary

## 1. **Directory Navigation with `os` Module**  
   - **Syntax**:  
     ```python  
     import os  
     book_dir = "./Books"  
     languages = os.listdir(book_dir)  # ['English', 'French', ...]  
     ```  
   - **Description**:  
     - Use `os.listdir()` to list subdirectories (e.g., languages).  
     - Navigate nested folders (language → author → title) using loops.  

## 2. **Reading Multiple Files with Nested Loops**  
   - **Syntax**:  
     ```python  
     for language in os.listdir(book_dir):  
         lang_path = os.path.join(book_dir, language)  
         for author in os.listdir(lang_path):  
             auth_path = os.path.join(lang_path, author)  
             for title in os.listdir(auth_path):  
                 title_path = os.path.join(auth_path, title)  
                 text = read_book(title_path)  
     ```  
   - **Description**:  
     - Uses `os.path.join()` to construct full file paths.  
     - Prints paths for debugging (`print(title_path)`).  

## 3. **Storing Statistics in a Pandas DataFrame**  
   - **Syntax**:  
     ```python  
     import pandas as pd  
     stats = pd.DataFrame(columns=["language", "author", "title", "length", "unique"])  
     title_num = 0  # Row index counter  
     # Inside loops:  
     stats.loc[title_num] = [  
         language,  
         author.capitalize(),  # Capitalize author names  
         title.replace(".txt", ""),  # Remove file extension  
         sum(counts),  # Total words  
         num_unique,    # Unique words  
     ]  
     title_num += 1  
     ```  
   - **Description**:  
     - Initialize an empty DataFrame with predefined columns.  
     - Populate rows dynamically using `.loc[]`.  

## 4. **Data Cleaning**  
   - **Syntax**:  
     ```python  
     # Capitalize author names and clean titles  
     author = author.capitalize()  
     title = title.replace(".txt", "")  
     ```  
   - **Example**:  
     - `"shakespeare"` → `"Shakespeare"`  
     - `"romeo_juliet.txt"` → `"romeo_juliet"`  

## 5. **Inspecting the DataFrame**  
   - **Syntax**:  
     ```python  
     stats.head()  # First 5 rows  
     stats.tail()  # Last 5 rows  
     ```  
   - **Output**:  
     - Displays structured data for quick validation.  

---

### Key Takeaways:  
1. **Directory Traversal**:  
   - Use nested loops with `os.listdir()` to process hierarchical file structures.  
2. **Dynamic DataFrame Population**:  
   - Increment row indices and use `.loc[]` to add entries efficiently.  
3. **Data Hygiene**:  
   - Clean metadata (e.g., capitalization, file extensions) during ingestion.  
4. **Pandas Utilities**:  
   - Leverage `.head()` and `.tail()` to inspect large datasets.  