---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [text-processing, python-dictionaries, data-analysis]  
---

# Summary

## 1. **Basic Word Counting Function**  
   - **Syntax**:  
     ```python  
     def count_words(text):  
         """Counts unique word frequencies using a dictionary."""  
         word_counts = {}  
         for word in text.split():  
             if word in word_counts:  
                 word_counts[word] += 1  
             else:  
                 word_counts[word] = 1  
         return word_counts  
     ```  
   - **Description**:  
     - Uses a dictionary to track word frequencies.  
     - Manual logic: checks if a word exists in the dictionary before incrementing.  

## 2. **Text Normalization**  
   - **Syntax**:  
     ```python  
     text = text.lower()  # Convert to lowercase  
     skip_chars = ['.', ',', ';', ':', "'", '"']  
     for char in skip_chars:  
         text = text.replace(char, '')  # Remove punctuation  
     ```  
   - **Description**:  
     - Converts text to lowercase to avoid case sensitivity.  
     - Strips punctuation using a predefined list of characters.  

## 3. **Optimized Function with Normalization**  
   - **Syntax**:  
     ```python  
     def count_words(text):  
         """Counts words after normalizing text (lowercase + punctuation removal)."""  
         text = text.lower()  
         skip_chars = ['.', ',', ';', ':', "'", '"']  
         for char in skip_chars:  
             text = text.replace(char, '')  
         word_counts = {}  
         for word in text.split():  
             word_counts[word] = word_counts.get(word, 0) + 1  
         return word_counts  
     ```  
   - **Example Output**:  
     ```python  
     test_text = "Hello! Hello, world."  
     print(count_words(test_text))  # {'hello': 2, 'world': 1}  
     ```  

## 4. **Using `Counter` from `collections`**  
   - **Syntax**:  
     ```python  
     from collections import Counter  
     def count_words_fast(text):  
         """Optimized word counting using `Counter`."""  
         text = text.lower()  
         skip_chars = ['.', ',', ';', ':', "'", '"']  
         for char in skip_chars:  
             text = text.replace(char, '')  
         return Counter(text.split())  
     ```  
   - **Description**:  
     - Replaces manual counting logic with `Counter` for efficiency.  
     - Returns a `Counter` object (subclass of dictionary).  

## 5. **Validation of Results**  
   - **Syntax**:  
     ```python  
     manual_result = count_words(test_text)  
     counter_result = count_words_fast(test_text)  
     print(manual_result == counter_result)  # True  
     ```  
   - **Description**:  
     - Confirms equivalence between manual and `Counter`-based methods.  

---

### Key Takeaways:  
1. **Text Cleaning**:  
   - Normalize text (lowercase + punctuation removal) to ensure accurate counts.  
2. **Dictionary vs. `Counter`**:  
   - `Counter` simplifies code and improves readability for frequency counting.  
3. **Efficiency**:  
   - Use `collections.Counter` for large datasets to leverage optimized performance.  
4. **Testing**:  
   - Validate implementations with test strings to catch edge cases (e.g., punctuation, case sensitivity).  