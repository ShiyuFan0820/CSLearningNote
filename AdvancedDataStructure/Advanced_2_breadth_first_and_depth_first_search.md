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

**Example**

Let's try to use stack to implement DFS traverse to the following tree:

<div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/fe6b25f9-81da-4f24-8c4b-0073ba409b00">
</div>

1. Start visiting the root node, cause node `20` has children, we add node `20` to the stack, keep visiting the left branch, node `10` has children, add node `10` to the stack, until visit node `4`, the leaf node:

<div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/6b2ff7f6-8593-48aa-a49b-9c440779435a">
</div>

2. Pop a node from the stack, the node is `10`, check if all children of node `10` has been visited, so we visit node `15`, as node `15` is also a leaf, we don't need to push any node to the stack:

<div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/9e37fd47-a997-4f8c-8a9c-d5c2fad54a8f">
</div>

3. Stack is not empty, keep popping a node from the stack, the node is `20`, check if all children of node `20` has been visited, node `30` has child, push node `30` into the stack, and visit its child `25`, node `25` is leaf:

<div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/17d1e6e3-dab3-4382-843f-43441963fc7f">
</div>

4. Pop a node from the stack, the node is `30`, node's child has been visit, stack is empty, the traverse ends:

<div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/23f0fa03-006f-4dee-a576-7ad86204ae50">
</div>

**Code Implementation**

## Breadth First Search

Breadth first search (BFS) is a traversal algorithm that explores all nodes at the current depth before moving on to nodes at the next depth level. BFS can be implemented by queue:
1. Start at visiting the starting node of the tree.
2. Use a queue to keep track of nodes need to be visited.
3. If the visited node has children, enqueque all children into the queue.
4. Dequeue a node from the queue to visit, repeat step 3.
5. While the queue is not empty, repeat the step 3 and 4.

**Code Implementation**

