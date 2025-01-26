---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [social-networks, network-analysis, networkx, empirical-data]  
---

# Summary

## 1. **Loading and Processing Empirical Network Data**  
   - **Data Source**: Adjacency matrices for two Indian village social networks (from micro-finance diffusion study).  
   - **Adjacency Matrix Structure**:  
     - Symmetric \( n \times n \) matrix (\( n = \text{number of nodes} \))  
     - \( A_{ij} = 1 \) if nodes \( i \) and \( j \) are connected, else \( 0 \).  
   - **Code Implementation**:  
     ```python  
     import numpy as np  
     import networkx as nx  

     # Load adjacency matrices  
     A1 = np.loadtxt("village1_adjacency.csv", delimiter=",")  
     A2 = np.loadtxt("village2_adjacency.csv", delimiter=",")  

     # Convert to NetworkX graphs  
     G1 = nx.from_numpy_array(A1)  
     G2 = nx.from_numpy_array(A2)  
     ```  

## 2. **Computing Network Statistics**  
   - **Function Definition** (updated for NetworkX ≥2.6):  
     ```python  
     def basic_net_stats(G):  
         n_nodes = G.number_of_nodes()  
         n_edges = G.number_of_edges()  
         degree_sequence = [d for n, d in G.degree()]  # Extract degrees from DegreeView  
         avg_degree = np.mean(degree_sequence)  

         print(f"Number of nodes: {n_nodes}")  
         print(f"Number of edges: {n_edges}")  
         print(f"Average degree: {avg_degree:.2f}")  
     ```  
   - **Results**:  
     - **Village 1**:  
       ```  
       Number of nodes: 843  
       Number of edges: 3400  
       Average degree: 8.06  
       ```  
     - **Village 2**:  
       ```  
       Number of nodes: 877  
       Number of edges: 3100  
       Average degree: 7.07  
       ```  

## 3. **Degree Distribution Analysis**  
   - **Observation**:  
     - Heavy-tailed distribution (many low-degree nodes, few highly connected nodes).  
     - Contrasts with Erdős-Rényi (ER) graphs, which show symmetric Poisson-like distributions.  
   - **Visualization Code**:  
     ```python  
     import matplotlib.pyplot as plt  

     def plot_degree_distribution(G, label):  
         degree_sequence = [d for n, d in G.degree()]  
         plt.hist(degree_sequence, bins=20, histtype="step", label=label, density=True)  

     plt.figure()  
     plot_degree_distribution(G1, "Village 1")  
     plot_degree_distribution(G2, "Village 2")  
     plt.xlabel("Degree ($k$)")  
     plt.ylabel("$P(k)$")  
     plt.legend()  
     plt.savefig("village_degree_histograms.pdf")  
     ```  

---

### Key Takeaways:  
1. **DegreeView Object Update**:  
   - Use `[d for n, d in G.degree()]` instead of `G.degree().values()` to extract degrees in NetworkX ≥2.6.  
2. **Empirical Network Properties**:  
   - Real-world social networks exhibit **scale-free-like** degree distributions (asymmetric, heavy-tailed).  
3. **ER Model Limitations**:  
   - ER graphs fail to capture the heterogeneity of real-world social connections.  
4. **Practical Workflow**:  
   - Load adjacency matrices → Convert to graphs → Compute statistics → Visualize distributions.  
5. **Interpretation**:  
   - Higher average degree in Village 1 suggests denser social interactions compared to Village 2.  