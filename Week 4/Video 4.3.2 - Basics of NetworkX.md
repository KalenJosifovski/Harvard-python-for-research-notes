---
Video path: (not specified)  
Subtitle path: (not specified)  
tags: [network-analysis, NetworkX, graph-theory]  
---

# Summary

## 1. **Graph Creation and Node Management**  
   - **Syntax**:  
     ```python  
     import networkx as nx  
     G = nx.Graph()  # Create an undirected graph  
     G.add_node("node1")  # Add single node  
     G.add_nodes_from([2, 3, "u", "v"])  # Add multiple nodes  
     ```  
   - **Description**:  
     - Nodes can be numbers, strings, or any hashable object.  
     - Use `G.nodes` to list all nodes: `['node1', 2, 3, 'u', 'v']`.  

## 2. **Edge Management**  
   - **Syntax**:  
     ```python  
     G.add_edge(1, 2)                # Add single edge  
     G.add_edges_from([(1, 3), (1, 4), ("u", "v"), ("u", "w")])  # Add multiple edges  
     ```  
   - **Description**:  
     - Edges auto-add missing nodes (e.g., adding edge `("u", "w")` creates node `"w"`).  
     - Use `G.edges` to list all edges.  

## 3. **Removing Nodes/Edges**  
   - **Syntax**:  
     ```python  
     G.remove_node(2)                # Remove single node  
     G.remove_nodes_from([4, 5])     # Remove multiple nodes  
     G.remove_edge(1, 3)             # Remove single edge  
     G.remove_edges_from([(1, 2), ("u", "v")])  # Remove multiple edges  
     ```  
   - **Result**:  
     - After removal, `G.nodes` and `G.edges` reflect updated graph structure.  

## 4. **Graph Properties**  
   - **Syntax**:  
     ```python  
     num_nodes = G.number_of_nodes()  # Total nodes  
     num_edges = G.number_of_edges()  # Total edges  
     ```  
   - **Example**:  
     - After adding nodes `[1, 2, 3, "u", "v", "w"]` and edges `[(1, 3), ("u", "w")]`:  
       ```python  
       print(num_nodes)  # 6  
       print(num_edges)  # 2  
       ```  

---

### Key Takeaways:  
1. **Flexible Node Types**:  
   - Nodes can be integers, strings, or any hashable Python object.  
2. **Dynamic Modification**:  
   - Add/remove nodes/edges dynamically with simple methods.  
3. **Auto-Node Creation**:  
   - Adding edges implicitly creates missing nodes.  
4. **Practical Use Cases**:  
   - Model social networks, transportation systems, or biological interactions.  