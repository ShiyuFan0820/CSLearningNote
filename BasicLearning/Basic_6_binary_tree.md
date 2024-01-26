# Binary Tree and Binary Search Tree

## Definition of Binary Tree and Binary Search Tree

**What is Binary Tree?**

In a Linked List, elements are stored in nodes and can be accessd in a single direction, a tree is a specialized form of a Linked List, the only difference is that a node can link one other node in a Linked List, but in a tree it can link multiple nodes, the nodes next the current node are called children nodes of the current node, the current node is called parent node, the root node is the node which doesn't have a parent, the node which doesn't have children is called leaf. 

A tree structure is more hierarchical structure, it can represent relationships in a more complex way compared to a simple linear linked list.

Binary tree is a specific type of trees, each node in a binary tree has at most two children nodes, the left subtree and right subtree, binary tree is widely used in computer science and algorithms due to its efficient structure for certain types of operations, such as searching, insertion, and deletion.

_Linked List:_

<div align=center>
<img width="500" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/5e53698e-6b98-4ab6-b56e-bc16d7bb59fd">
</div>

_Tree structure:_

<div align=center>
<img width="500" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/23d81fff-d318-4653-bb6e-72a284ac566b">
</div>

_Binary tree:_

<div align=center>
<img width="450" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/1fbad6b0-9b33-4899-8d87-255d14717e9e">
</div>

**What is Binary Search Tree?**

Binary search tree is a specific binary tree, it just has one additional rule that is every node's value must be more than its left child's value and less than its right child's value, this is the rule to validate whether a binary search tree is valid.

_Valid binary search tree:_

<div align=center>
<img width="380" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/22da0f1b-3706-4250-848e-d6b390f39e4d">
</div>

_Invalid binary search tree:_

<div align=center>
<img width="600" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/35b53a2a-0db3-4f2a-8c4f-efc21aeff486">
</div>

## Time Complexity of Binary Tree

**Height of a Binary Tree:**

Height of a node is the longest distance from the node to a leaf, and hight of a tree is the longest distance from the root to a leaf.

<div align=center>
<img width="500" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/15571402-2331-41a2-87be-aec9accb4040">
</div>

**Depth of a Binary Tree:**

The depth of a node is the length of the path from the root to that node. The depth of a binary tree is the maximum depth among all nodes in the tree.

<div align=center>
<img width="650" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/3963908c-00fe-4aa2-b6ca-65a1d77e4e6d">
</div>

**Tree Balance:**

The balance of a tree often refers to whether the tree is maintaining a relatively even distribution of nodes in the left and right subtrees. A balanced tree is a tree in which the height of the two subtrees of any node differs by no more than one, if it's more than one, the tree is considered unbalanced.

**Time Complexity of Bianry Tree:**

_Two extreme balance situations:_

<div align=center>
<img width="700" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/4898a92c-323e-4218-91ec-5d632d6fc225">
</div>

The two binary trees shows the worst and best cases in the binary tree structure.

The worst case is just like a linked list, when we want to insert, delete or find a node, we have to traverse over all nodes, the time complexity of this case is O(n).

The best case is like a binary search tree, and it almost doubled the number of nodes in the next row, when the numbers of nodes are equal to 7, the depth of the tree is 3, and when we add another row which means we add to 15 nodes, the depth of the tree is 4, we can find the relationship between nodes and depth is _log<sub>2</sub><sup>(n+1)</sup>_, so the complexity of the best case is _O(log<sup>n</sup>)_.

In conclusion, binary search tree is efficient for searching, inserting and deleting by exploiting the ordering property.

## Binary Search Tree Implementation in Python
```py
class NODES:
    def __init__(self, val):
        self.m_value = val
        self.m_next_left = None
        self.m_next_right = None


class BST:
    def __init__(self):
        self.m_root = None
    
    def insert(self, val):
        pass
    
    def delete(self, val):
        pass
    
```
