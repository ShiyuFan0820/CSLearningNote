# Breadth First and Depth First Search

Breadth first and depth first search are graph traversal methods used to traverse or visit all the vertices (nodes) in a graph, a graph is a data structure that consists of a set of vertices (also called nodes) and a set of edges that connect pairs of vertices.

<div align=center>
<img width="350" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/736eec7c-77d7-4942-8872-c7cc11bd16c7">
</div>

## Depth First Search

Depth first search (DFS) is a traversal algorithm that explores as far as possible along each branch before backtracking. Depth first search can be implemented by using stack data structure, this is how DFS works by using the stack:

1. Start with an empty stack and push the selected starting vertex into the stack.
2. While the stack is not empty, continue the folloing steps:
 - Pop a vertex from the stack.
 - Visit the popped vertex.
 - Push all unvisited neighbors of the popped vertex onto the stack.
Repeat until there are no unvisited neighbors left.

## Breadth First Search

Breadth first search (BFS) is a traversal algorithm that explores all nodes at the current depth before moving on to nodes at the next depth level. BFS can be implemented by queue:
1. Start at a selected starting vertex of the graph.
2. Use a queue to keep track of vertices to visit, enqueue the selected vertex.
3. While the queue is not empty, continue the following steps:
 - Dequeue a vertex from the queue.
 - Visit the dequeued vertex.
 - Enqueue all unvisited neighbors of the dequeued vertex.


