# Graph Theory

## Introduction

[Graph Theory](https://www.baeldung.com/cs/graph-theory-intro#8-the-weighted-graph) is a branch of mathematics and computer science that studies the properties of graphs. A graph consists of vertices (or nodes) and edges (or arcs) that connect pairs of vertices. In short, a graph is defined as $G = (V, E)$, where $V$ is a set of nodes (also called vertices) and $E$ is a set of edges (also called links).

![alt text](./images/graphs-set.webp)

## Components of a Graph

**Vertices** are the fundamental units of graphs and can represent entities such as cities, people, or points in space. The **degree of a vertex** in an undirected graph is the number of edges connected to it. In directed graphs, this is split into the indegree (number of edges directed into the vertex) and outdegree (number of edges directed out of the vertex). Another important component of a graph is the **edge**. Edges connect pairs of vertices and can represent relationships like roads between cities, friendships between people, etc. There are different types of graphs, which we will look into in the next section.
A **subgraph** is formed from a subset of the vertices and edges of a graph. A **path** is a sequence of edges that connect a sequence of vertices. A path that starts and ends at the same vertex, with no repeated edges or vertices (except the starting/ending vertex), is called a **cycle**.


## Types of Graphs

### Directed and Undirected Graphs

Directed Graphs are those whose edges have a direction, indicating a one-way relationship. Directed graphs have the characteristic that they model real-world relationships well, for which we cannot freely interchange the subject and the object. Undirected graphs are those whose edges do not have a direction. The edges indicate a two-way relationship in that each edge can be traversed in both directions. As a general rule, if we are not sure whether a graph should be directed or undirected, then the graph is directed. Undirected Graphs are those whose edges do not have a direction. Undirected graphs allow their traversal between any two vertices connected by an edge. The same is not necessarily true for directed graphs.

Directed Acyclic Graph (DAG) is an incredibly valuable instrument for representing and managing the relationships and dependencies among various tasks that need to be scheduled. In such a graph, each node represents a task, and the directed edges between these nodes indicate the precedence relationships, meaning that one task must be completed before another can begin. 

In DAGs used for scheduling, each node represents an individual task or task. These tasks often have associated attributes like duration, resource requirements, or deadlines. The directed edges between the nodes represent the precedence constraints. An edge from node A to node B implies that task A must be completed before task B can start. This directionality is critical for ensuring tasks are performed in the correct order. The acyclic property of DAGs is crucial in scheduling because it guarantees that there are no circular dependencies, which would make scheduling impossible. In practical terms, this means there can be no situation where task A depends on task B while task B simultaneously depends on task A, either directly or indirectly.

![alt text](./images/application.png)

*Figure 2: A directed acyclic graph (DAG) shows precedences, showing that process 1 must complete before processes 2 and 3 can be started, etc.*

### Weighted and Unweighted Graphs

Weighted Graphs are those whose edges have weights or costs associated with them, which can represent distance, cost, or any other metric that needs to be tracked. A typical weighted graph commonly used in machine learning is an artificial neural network. We can conceptualize neural networks as directed weighted graphs on which each vertex has an extra activation function assigned to it. Unweighted graphs are those whose edges do not have any weights associated with them.

### Connected and Disconnected Graphs

We can also discriminate graphs on the basis of the characteristics of their paths. For example, we can discriminate according to whether there are paths that connect all pairs of vertices, or whether there are pairs of vertices that do not have any paths between them. We call a graph connected if there is at least one path between any two of its vertices. Similarly, we say that a graph is disconnected if there are at least two vertices separated from one another.


## Graphs And NetworkX
Graph operations are fundamental to manipulating and analyzing data structured as graphs. In Python, you can manage these operations using libraries like NetworkX, which provides comprehensive support for creating and manipulating graphs. Here is a breakdown of common graph operations and the necessary APIs to perform them in Python using NetworkX. Below are some operations that are performed on graphs as part of the lab:
- Creating an empty graph
``` BASH
import networkx as nx

# Create a directed graph
D = nx.DiGraph()
```
- Insertion of Nodes/Edges in the graph: Insert a node or edge into the graph.
``` BASH
# Insert a single node
G.add_node(1)
# Insert an edge between node 1 and 2
G.add_edge(1, 2)
```
- Deletion of Nodes/Edges in the graph: Delete a node from the graph.
``` BASH
# Remove a node
G.remove_node(2)

# Remove an edge between 1 and 3
G.remove_edge(1, 3)
```
- Reading Graph Data: Read graph data from various formats such as JSON. For example, the  **application_data** is a python dictionary that already contains details of tasks and their interdependencies. You have to create the graph networkx from this application_data.
- Searching on Graphs: Search an entity in the graph.
``` BASH
# Use BFS to find all nodes reachable from node 1
reachable_from_1 = list(nx.bfs_edges(G, 1))
```
- Sorting Graph Data: Sorting is not a direct operation in graph theory as it is in array manipulation, but you might sort nodes or edges based on attributes like degree, weight, etc.
``` BASH
# Sort nodes by degree
sorted_nodes_by_degree = sorted(G.nodes(), key=lambda x: G.degree(x))
```
 

## Graph Traversal Algorithms

Some of the commonly used graph traversal algorithms are [Breadth First Search (BFS)](https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/) and Depth First Search (DFS) algorithms. BFS starts at a root node and explores all neighbors at the present depth before moving on to nodes at the next depth level. It uses a queue to keep track of the next vertex to start a search when a dead end is reached in any iteration. BFS finds the shortest path in an unweighted graph. In networking, BFS is used for broadcasting packets of information to all nodes of a network. [DFS](https://www.geeksforgeeks.org/depth-first-search-or-dfs-for-a-graph/) uses a stack to explore as far as possible along each branch before backtracking. It goes deep into a graph by exploring a node's children before visiting its siblings.

## Traversing Shortest Path in a Graph

Algorithms like Dijkstra's Algorithm find the shortest path from a single source to all other vertices in a graph. Also, the Bellman-Ford Algorithm computes the shortest paths from a single source vertex to all of the other vertices in a graph with edge weights that may be negative. An algorithm that efficiently combines both Dijkstra and Bellman-Ford algorithms is called Johnson's Algorithm.

                        
## Minimum Spanning Tree of a graph
[Minimum Spanning Tree (MST)](https://www.geeksforgeeks.org/prims-minimum-spanning-tree-mst-greedy-algo-5/) of a graph is a fundamental concept in graph theory used primarily in network design and optimization. The MST is a subset of the edges of a weighted, undirected graph that connects all the vertices without any cycles and with the minimal possible total edge weight. This tree spans all the vertices in the graph, meaning that every vertex is included, making it a spanning tree. The minimum aspect refers to the sum of the weights of the edges in the tree being as small as possible. There are several algorithms available to find an MST in a graph, with Kruskal's Algorithm and Prim's Algorithm being the most prominent. Consider a graph where the vertices represent cities, and the edges represent possible roads between them, with weights indicating the cost to build. An MST would provide a way to connect all the cities while minimizing the total construction cost. This could be crucial for governmental budgeting and planning in infrastructure projects.