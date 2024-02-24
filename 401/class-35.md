# Class 35 Reading Notes: Graphs

### Graph Basics
- **Graph**: A collection of nodes (vertices) connected by edges.
- **Vertex (Node)**: A data point in a graph.
- **Edge**: A connection between two vertices.
- **Neighbor**: An adjacent vertex connected by an edge.
- **Degree**: Number of edges connected to a vertex.

### Types of Graphs
- **Undirected Graph**: Edges have no direction. Connections are bi-directional.
- **Directed Graph (Digraph)**: Edges have a specified direction from one vertex to another.
- **Complete Graph**: Every vertex is connected to every other vertex.
- **Connected Graph**: There is at least one path between every pair of vertices.
- **Disconnected Graph**: Not all vertices are connected; some may be isolated.
- **Acyclic Graph**: A graph with no cycles (paths that start and end at the same vertex).
- **Cyclic Graph**: A graph that contains at least one cycle.

### Graph Representation
- **Adjacency Matrix**: A 2D array where rows and columns represent vertices and cell values indicate if an edge exists (1) or not (0).
- **Adjacency List**: A list where each vertex has a list of all vertices it's connected to.

### Weighted Graphs
- **Weighted Graph**: Edges have weights representing the cost or distance between vertices.
- **Weight Matrix**: Similar to an adjacency matrix, but cell values represent edge weights.
- **Weighted List**: An adjacency list that includes edge weights alongside connected vertices.

### Graph Traversals
- **Breadth-First Search (BFS)**: Visits all the neighbors of a vertex before moving to their neighbors. Uses a queue to keep track of the order.
- **Depth-First Search (DFS)**: Explores as far as possible along each branch before backtracking. Uses a stack to navigate through vertices.

### Real-World Applications
- GPS and Mapping
- Social Networks
- Airline Traffic
- Recommendations (e.g., Netflix suggestions)

### Notes
- In an undirected graph, the adjacency matrix is symmetric.
- For weighted graphs, the adjacency matrix or list represents edge weights instead of simply indicating the presence of edges.
- Traversal algorithms require mechanisms to track visited vertices to prevent cycles from causing infinite loops.