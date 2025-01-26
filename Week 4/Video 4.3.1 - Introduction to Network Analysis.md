---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [network-analysis, graph-theory, python]  
---

# Summary

## 1. **Basic Network Concepts**  
   - **Definition**:  
     - **Nodes (Vertices)**: Represent entities (e.g., people, genes).  
     - **Edges (Links)**: Represent interactions between nodes.  
     - **Degree**: Number of edges connected to a node.  
     - **Path**: Sequence of nodes where consecutive nodes are connected (e.g., node 1 → 2 → 3).  
   - **Example**:  
     ```python  
     import networkx as nx  
     G = nx.Graph()  
     G.add_edges_from([(1, 2), (2, 3)])  # Nodes 1-2-3 form a path of length 2  
     print("Degree of node 2:", G.degree[2])  # Output: 2  
     ```  

## 2. **Graph Properties**  
   - **Connected vs. Disconnected**:  
     - **Connected**: All nodes are reachable from each other.  
     - **Disconnected**: Contains isolated components (subgraphs with no connections between them).  
   - **Components**:  
     - **Largest Connected Component (LCC)**: Subgraph with the most nodes.  
   - **Example**:  
     ```python  
     # Check connectivity  
     print("Is connected:", nx.is_connected(G))  # Output: True  
     # Add disconnected nodes  
     G.add_nodes_from([4, 5])  
     components = list(nx.connected_components(G))  
     print("Components:", components)  # Output: [{1, 2, 3}, {4}, {5}]  
     ```  

## 3. **Applications of Network Analysis**  
   - **Social Networks**: Track disease spread or information diffusion.  
   - **Biological Networks**: Study protein interactions or gene regulation.  
   - **Infrastructure**: Model power grids or transportation systems.  
   - **Example**:  
     ```python  
     # Simulate social network with 100 nodes  
     social_network = nx.erdos_renyi_graph(n=100, p=0.1)  
     print("LCC size:", len(max(nx.connected_components(social_network), key=len)))  
     ```  

## 4. **Visualising Networks**  
   - **Syntax**:  
     ```python  
     import matplotlib.pyplot as plt  
     nx.draw(G, with_labels=True, node_color='lightblue', edge_color='gray')  
     plt.title("Simple Network Graph")  
     plt.savefig("network_graph.png")  
     plt.show()  
     ```  
   - **Key Features**:  
     - Customise node/edge colors and labels.  
     - Export plots for reports or publications.  

---

### Key Takeaways:  
1. **Terminology**:  
   - Use "nodes" and "edges" to model systems (e.g., friendships in social networks).  
2. **Connectivity**:  
   - Critical for robustness analysis (e.g., how many node failures disconnect the network).  
3. **Tools**:  
   - Libraries like `networkx` simplify graph creation, analysis, and visualization.  
4. **Applications**:  
   - Identify influential nodes (high degree) in social networks or bottlenecks in infrastructure.  