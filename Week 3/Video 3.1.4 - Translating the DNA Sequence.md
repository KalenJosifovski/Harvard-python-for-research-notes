---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [python-file-io, data-cleaning, bioinformatics]  
---

# Summary

## 1. **Codon-to-Amino Acid Translation Table**  
   - **Syntax**:  
     ```python  
     table = {  
         'CAA': 'Q',  # Glutamine  
         'CCT': 'P',  # Proline  
         'GTA': 'V',  # Valine  
         # ... other codons  
     }  
     ```  
   - **Description**:  
     - A dictionary maps 3-letter DNA codons to 1-letter amino acid symbols.  
     - Keys are codon strings (e.g., `'CAA'`), values are amino acids (e.g., `'Q'`).  

## 2. **Sequence Length Validation**  
   - **Syntax**:  
     ```python  
     if len(sequence) % 3 != 0:  
         raise ValueError("Sequence length must be divisible by 3.")  
     ```  
   - **Description**:  
     - Use the modulo operator (`%`) to ensure the DNA sequence length is a multiple of 3.  
     - Critical for accurate codon grouping.  

## 3. **Looping Through Codons**  
   - **Syntax**:  
     ```python  
     for i in range(0, len(sequence), 3):  
         codon = sequence[i:i+3]  
     ```  
   - **Description**:  
     - Iterate over the sequence in steps of 3 using `range()`.  
     - Extract each codon using string slicing.  

## 4. **String Slicing for Codon Extraction**  
   - **Syntax**:  
     ```python  
     codon = sequence[start:end]  # e.g., sequence[0:3]  
     ```  
   - **Example**:  
     ```python  
     codon1 = sequence[0:3]  # First codon  
     codon2 = sequence[3:6]  # Second codon  
     ```  

## 5. **Building the Protein String**  
   - **Syntax**:  
     ```python  
     protein = ""  
     codon = "CAA"  
     protein += table[codon]  # Append amino acid  
     ```  
   - **Description**:  
     - Start with an empty string and concatenate amino acids iteratively.  
     - Use `table.get(codon, "?")` to handle unknown codons (returns `"?"` as default).  

## 6. **Function Definition with Docstrings**  
   - **Syntax**:  
     ```python  
     def translate(sequence):  
         """  
         Translates DNA sequence to protein.  
         Args:  
             sequence (str): DNA sequence (length divisible by 3).  
         Returns:  
             str: Protein string.  
         """  
         # Implementation here  
     ```  
   - **Description**:  
     - Wrap translation logic in a reusable function.  
     - Include a docstring for documentation (accessible via `help(translate)`).  

## 7. **Placeholder `pass` Statement**  
   - **Syntax**:  
     ```python  
     if len(sequence) % 3 == 0:  
         pass  # Placeholder for future code  
     ```  
   - **Description**:  
     - Use `pass` to avoid syntax errors in incomplete code blocks.  

---

### Key Takeaways:  
1. **Dictionary Lookup**:  
   - Efficiently map codons to amino acids using a pre-defined dictionary.  
2. **Validation**:  
   - Ensure sequence length is valid with `len(sequence) % 3 == 0`.  
3. **Iteration**:  
   - Use `range(0, len(sequence), 3)` to process codons sequentially.  
4. **Function Design**:  
   - Encapsulate logic in functions with clear docstrings for reusability.  
5. **Error Handling**:  
   - Use `get(codon, "?")` to gracefully handle missing codons.  