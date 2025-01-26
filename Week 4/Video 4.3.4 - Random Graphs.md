---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [network-analysis, random-graphs, NetworkX]  
---

# Summary

## 1. **Erdős-Rényi (ER) Model Overview**  
   - **Parameters**:  
     - `N`: Number of nodes.  
     - `p`: Probability of an edge between any two nodes.  
   - **Process**:  
     - Start with `N` nodes and no edges.  
     - For each node pair `(i, j)` where `i < j`, add an edge with probability `p`.  

## 2. **Implementing the ER Model**  
   - **Step 1: Create Graph and Add Nodes**  
     ```python  
     import networkx as nx  
     from scipy.stats import bernoulli  
      
     def ER_graph(N, p):  
         """Generates an Erdős-Rényi random graph."""  
         G = nx.Graph()  
         G.add_nodes_from(range(N))  # Add N nodes (0 to N-1)  
     ```  

   - **Step 2: Add Edges with Probability `p`**  
     ```python  
         for i in range(N):  
             for j in range(i + 1, N):  # Avoid duplicate pairs (i < j)  
                 if bernoulli.rvs(p):    # Bernoulli trial with success prob. p  
                     G.add_edge(i, j)  
         return G  
     ```  
   - **Key Fix**: Looping over `i < j` ensures each node pair is checked **once**, avoiding duplicate edges.  

## 3. **Generating and Visualizing the Graph**  
   - **Example Usage**:  
     ```python  
     import matplotlib.pyplot as plt  
      
     G = ER_graph(N=50, p=0.08)  # Generate graph with 50 nodes  
     nx.draw(G, node_size=40, node_color="gray", with_labels=False)  
     plt.savefig("er_graph.pdf")  
     ```  
   - **Output**:  
     - A sparse graph (for small `p`) or dense graph (for large `p`).  

## 4. **Edge Probability and Graph Density**  
   - **Expected Edge Count**:  
     $$ \text{Expected edges} = \frac{N(N-1)}{2} \cdot p $$  
   - **Example**:  
     - For `N=50`, `p=0.08`: Expected edges ≈ 98.  

---

### Key Takeaways:  
1. **Avoiding Duplicate Edges**:  
   - Loop over `i < j` instead of all pairs to comply with undirected graph conventions.  
2. **Bernoulli Trials**:  
   - Use `bernoulli.rvs(p)` to simulate edge creation with probability `p`.  
3. **Practical Use**:  
   - Model social networks, communication networks, or disease spread.  
4. **NetworkX Integration**:  
   - Custom implementations complement built-in generators (e.g., `nx.erdos_renyi_graph`).  