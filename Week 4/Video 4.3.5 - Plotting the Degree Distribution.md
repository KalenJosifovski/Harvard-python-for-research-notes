---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [network-analysis, degree-distribution, networkx, matplotlib]  
---

# Summary

## 1. **Function Definition for Degree Distribution Plotting**  
   - **Purpose**: Plot the degree distribution of a graph using a step histogram.  
   - **Updated Syntax** (for NetworkX ≥2.6):  
     ```python  
     import matplotlib.pyplot as plt  

     def plot_degree_distribution(G):  
         # Extract degree sequence from DegreeView object  
         degree_sequence = [d for n, d in G.degree()]  
         # Create step histogram  
         plt.hist(degree_sequence, bins=15, histtype="step", density=True)  
         plt.xlabel("Degree ($k$)")  
         plt.ylabel("$P(k)$")  
         plt.title("Degree Distribution")  
         plt.grid(True)  
     ```  

## 2. **Implementation Steps**  
   - **Generate Graph**:  
     ```python  
     import networkx as nx  

     # Example: Erdős-Rényi graph with 500 nodes  
     G = nx.erdos_renyi_graph(n=500, p=0.08)  
     ```  
   - **Plot Degree Distribution**:  
     ```python  
     plot_degree_distribution(G)  
     plt.savefig("degree_histogram.pdf")  # Save as PDF  
     plt.show()  
     ```  

## 3. **Example Outputs**  
   - **Small Graph (n=50)**:  
     - Sparse distribution with degrees ranging from 0 to ~10.  
     - Less clear pattern due to limited sample size.  
   - **Large Graph (n=500)**:  
     - Tighter distribution (degrees between ~25–65).  
     - Bell-shaped curve typical of Erdős-Rényi graphs.  
   - **Multiple Realizations**:  
     ```python  
     # Generate and plot 3 different graphs  
     for i in range(3):  
         G = nx.erdos_renyi_graph(n=500, p=0.08)  
         plot_degree_distribution(G)  
         plt.savefig(f"degree_histogram_{i}.pdf")  
         plt.clf()  # Clear plot for next iteration  
     ```  
     - Slight variations in degree distributions due to stochasticity.  

---

### Key Takeaways:  
1. **DegreeView Object Update**:  
   - `G.degree()` in NetworkX returns a `DegreeView` (iterable of `(node, degree)` tuples). Use `[d for n, d in G.degree()]` to extract degrees.  
2. **Graph Size Impact**:  
   - Larger graphs produce smoother, more interpretable degree distributions.  
3. **Erdős-Rényi Behavior**:  
   - Degree distributions approximate a Poisson distribution for large `n`.  
4. **Visualization Flexibility**:  
   - Step histograms (`histtype="step"`) avoid overplotting and highlight distribution trends.  
5. **Reproducibility**:  
   - Use `nx.erdos_renyi_graph(n, p)` with fixed seeds for consistent comparisons.  