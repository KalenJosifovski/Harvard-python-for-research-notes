---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [machine-learning, algorithms, voting]  
---

# Summary

## 1. **Manual Majority Vote Implementation**  
   - **Syntax**:  
     ```python  
     import random  
     def majority_vote(votes):  
         """  
         Returns the most frequent element in a list, with random tie-breaking.  
         Args:  
             votes (list): Sequence of votes (e.g., [1, 2, 3, 1, 2]).  
         Returns:  
             Any: Most frequent element.  
         """  
         vote_counts = {}  
         for vote in votes:  
             if vote in vote_counts:  
                 vote_counts[vote] += 1  
             else:  
                 vote_counts[vote] = 1  
         max_count = max(vote_counts.values())  
         winners = [vote for vote, count in vote_counts.items() if count == max_count]  
         return random.choice(winners)  
     ```  
   - **Description**:  
     - Counts occurrences of each vote using a dictionary.  
     - Identifies all elements with the highest count and breaks ties randomly.  

## 2. **Handling Ties with Random Selection**  
   - **Example**:  
     ```python  
     votes = [1, 2, 3, 1, 2, 3, 3]  # 3 is the majority  
     print(majority_vote(votes))  # Output: 3  

     tied_votes = [1, 2, 1, 2, 3]  # Ties between 1 and 2  
     print(majority_vote(tied_votes))  # Randomly returns 1 or 2  
     ```  
   - **Description**:  
     - In tied cases (e.g., two votes with the same count), `random.choice` ensures unbiased selection.  

## 3. **Using SciPy’s Mode Function**  
   - **Syntax**:  
     ```python  
     from scipy import stats  
     def majority_vote_scipy(votes):  
         """Returns mode of votes (no random tie-breaking)."""  
         return stats.mode(votes)[0][0]  
     ```  
   - **Example**:  
     ```python  
     print(majority_vote_scipy([1, 2, 2, 3]))  # Output: 2  
     print(majority_vote_scipy([1, 2, 1, 2]))  # Output: 1 (arbitrary tie-breaking)  
     ```  
   - **Limitation**:  
     - SciPy’s `mode` returns the smallest element in ties, not random.  

---

### Key Takeaways:  
1. **Custom Tie-Breaking**:  
   - Manual implementation allows random selection in tied cases, critical for unbiased KNN classification.  
2. **Library Shortcuts**:  
   - SciPy’s `stats.mode` is efficient but unsuitable for randomized tie resolution.  
3. **Function Design**:  
   - Prefer manual counting for flexibility in handling edge cases (e.g., ties).  