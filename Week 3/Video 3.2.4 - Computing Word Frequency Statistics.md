---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [text-processing, data-analysis, python-dictionaries]  
---

# Summary

## 1. **Word Statistics Function**  
   - **Syntax**:  
     ```python  
     def word_stats(word_counts):  
         """  
         Returns unique word count and frequency list from a word-count dictionary/Counter.  
         Args:  
             word_counts (dict/Counter): {word: count} pairs.  
         Returns:  
             tuple: (num_unique_words, list_of_counts)  
         """  
         num_unique = len(word_counts)  
         counts = list(word_counts.values())  
         return (num_unique, counts)  
     ```  
   - **Description**:  
     - `len(word_counts)` gives the number of unique words.  
     - `word_counts.values()` extracts frequencies of all words.  

## 2. **Calculating Total Words**  
   - **Syntax**:  
     ```python  
     total_words = sum(counts)  # Sum frequencies from word_stats output  
     ```  
   - **Example**:  
     ```python  
     text = read_book("shakespeare_romeo_juliet.txt")  
     word_counts = count_words(text)  
     num_unique, counts = word_stats(word_counts)  
     print(f"Unique words: {num_unique}")  # 5118 for English Romeo and Juliet  
     print(f"Total words: {sum(counts)}")   # ~41,000 total words  
     ```  

## 3. **Comparing Language-Specific Text Statistics**  
   - **Example Workflow**:  
     ```python  
     # English version  
     eng_text = read_book("english/Shakespeare/Romeo_and_Juliet.txt")  
     eng_counts = count_words(eng_text)  
     eng_unique, eng_freq = word_stats(eng_counts)  

     # German version  
     ger_text = read_book("german/Shakespeare/Romeo_und_Julia.txt")  
     ger_counts = count_words(ger_text)  
     ger_unique, ger_freq = word_stats(ger_counts)  

     print(f"English: {eng_unique} unique, {sum(eng_freq)} total")  
     print(f"German: {ger_unique} unique, {sum(ger_freq)} total")  
     ```  
   - **Output Insight**:  
     - German translations often use more unique words (e.g., 7,500 vs. 5,118) due to compound words.  

---

### Key Takeaways:  
1. **Unique vs. Total Words**:  
   - `len(word_counts)` for unique words; `sum(counts)` for total words.  
2. **Language Analysis**:  
   - Compare metrics like unique word density to study linguistic features (e.g., German’s compound words).  
3. **Flexible Input**:  
   - Works with both dictionaries and `collections.Counter` objects.  