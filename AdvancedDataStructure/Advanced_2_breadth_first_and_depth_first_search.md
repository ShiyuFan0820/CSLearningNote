# Breadth First and Depth First Search

Breadth first and depth first search are two traversal methods used to traverse or visit all the nodes in a tree structure.

## Depth First Search

Depth first search (DFS) is a traversal algorithm that explores as far as possible along each branch before backtracking. Depth first search can be implemented by using stack data structure, this is how DFS works by using the stack:

1. Start with an empty stack to keep track of the nodes to be visited, start by visiting the starting node of the tree.
2. If the node has children push the node into the stack, and visit one of its children, until the leaf node is visited.
3. Pop a node from the stack, check if all the children of the node have been visited.
4. If not, visit another child and repeat the step 2.
5. If all children of the node have been visited, repeat step 3.
6. Visit stops if the stack is empty.

**Code Implementation**

## Breadth First Search

Breadth first search (BFS) is a traversal algorithm that explores all nodes at the current depth before moving on to nodes at the next depth level. BFS can be implemented by queue:
1. Start at visiting the starting node of the tree.
2. Use a queue to keep track of nodes need to be visited.
3. If the visited node has children, enqueque all children into the queue.
4. Dequeue a node from the queue to visit, repeat step 3.
5. While the queue is not empty, repeat the step 3 and 4.

**Code Implementation**

