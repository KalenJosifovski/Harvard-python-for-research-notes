---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [bioinformatics, data-download, ncbi]  
---

# Summary

## 1. **Accessing NCBI Data**  
   - **Website**: Visit [NCBI](https://www.ncbi.nlm.nih.gov/) and search under the **Nucleotide** database.  
   - **Search Code**: Enter `NM_207618.2` (case-sensitive) to locate the specific DNA sequence.  

## 2. **Downloading DNA Sequence**  
   - **Steps**:  
     1. Click **FASTA** to view the DNA sequence in FASTA format.  
     2. Select and copy the entire sequence (from the first "G" to the last "T").  
     3. Paste into a text editor (e.g., Spyder) and save as `dna.txt` in a dedicated directory (e.g., `python_case_studies/translation`).  

## 3. **Downloading Protein Sequence**  
   - **Steps**:  
     1. Return to the NCBI sample page and click **CDS** (Coding Sequence).  
     2. Copy the translated amino acid sequence from the pop-up window.  
     3. Save as `protein.txt` in the same directory.  

## 4. **File Organization**  
   - **Naming Conventions**:  
     - DNA file: `dna.txt`  
     - Protein file: `protein.txt`  
   - **Directory Structure**:  
     ```  
     python_case_studies/  
     └── translation/  
         ├── dna.txt  
         └── protein.txt  
     ```

---

### Key Takeaways:  
1. **NCBI Workflow**:  
   - Use exact codes (e.g., `NM_207618.2`) for precise data retrieval.  
   - FASTA format provides raw DNA sequences; CDS provides translated protein sequences.  
2. **Data Integrity**:  
   - Ensure the entire sequence is copied (no truncated ends).  
   - Validate file extensions (`.txt`) to avoid format errors.  
3. **Preparation for Analysis**:  
   - Properly organized files streamline subsequent tasks (e.g., DNA translation in Python).  