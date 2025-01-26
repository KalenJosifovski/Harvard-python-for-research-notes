---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [network-analysis, connected-components, NetworkX]  
---

# Summary

## 1. **Finding Connected Components**  
   - **Syntax**:  
     ```python  
     import networkx as nx  
     components = nx.connected_components(G)  # Generator for node sets of components  
     ```  
   - **Description**:  
     - A connected component is a subgraph where all nodes are reachable via edges.  
     - `nx.connected_components` returns a generator of node sets for each component.  

## 2. **Extracting the Largest Connected Component (LCC)**  
   - **Syntax**:  
     ```python  
     # Get node set of the largest component  
     lcc_nodes = max(nx.connected_components(G), key=len)  
     # Create subgraph from the LCC nodes  
     G_lcc = G.subgraph(lcc_nodes)  
     ```  
   - **Example**:  
     ```python  
     G = nx.karate_club_graph()  
     lcc_nodes = max(nx.connected_components(G), key=len)  
     G_lcc = G.subgraph(lcc_nodes)  
     print(f"LCC size: {len(G_lcc)} nodes")  # Output: 34 nodes (karate club is fully connected)  
     ```  

## 3. **Calculating LCC Proportion**  
   - **Syntax**:  
     ```python  
     lcc_proportion = len(G_lcc) / G.number_of_nodes()  
     ```  
   - **Application**:  
     - Example: If `G` has 843 nodes and `G_lcc` has 825, `lcc_proportion ≈ 0.979`.  

## 4. **Visualising the LCC**  
   - **Syntax**:  
     ```python  
     import matplotlib.pyplot as plt  
     nx.draw(G_lcc, node_size=20, node_color="red", edge_color="gray", with_labels=False)  
     plt.savefig("lcc_visualization.pdf")  
     ```  
   - **Output**:  
     - A plot highlighting the largest connected subgraph.  

---

### Key Takeaways:  
1. **LCC Significance**:  
   - Most real-world networks (e.g., social/media graphs) have a dominant LCC containing >90% of nodes.  
2. **Deprecated Functions**:  
   - Avoid `nx.connected_component_subgraphs` (deprecated); use `nx.connected_components` with `subgraph()`.  
3. **Practical Use Cases**:  
   - Measure network robustness (e.g., how many nodes remain connected if edges fail).  
   - Identify communities or critical hubs in infrastructure.  
4. **Performance Note**:  
   - Use generators (`nx.connected_components`) for memory efficiency with large graphs.  