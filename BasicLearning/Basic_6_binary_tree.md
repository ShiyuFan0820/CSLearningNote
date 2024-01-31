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

To create a bianry search tree we can use iteration and recursion, to traverse in a binary search tree, there are three visiting method -- pre-order, in-order and post-order. 

The visiting order of pre-order is that for each subtree firstly visit the root, then the left subtree, and lastly the right subtree, each node is visited before its children.

The visiting order of in-order is a acsending order of their value, for each subtree it starts from the leftmost node (the one with the smallest value), then the root value and lastly goes to the rightmost node (the one with the largest value).

The visiting order of post-order is for each subtree, it starts from the left most node, then the rightmost node, lastly the root.

_The code is:_
```py
# Using iteration:
class NODES:
    def __init__(self, val):
        self.m_value = val
        self.m_lchild = None
        self.m_rchild = None


class BST:
    def __init__(self):
        self.m_root = None

    def is_empty(self):
        if not self.m_root:
            return not self.m_root

    def insert(self, val):
        new_node = NODES(val)
        if self.is_empty():
            self.m_root = new_node
        else:
            current_node = self.m_root
            while True:
                if val <= current_node.m_value:
                    if current_node.m_lchild is None:
                        current_node.m_lchild = new_node
                        break
                    else:
                        current_node = current_node.m_lchild
                else:
                    if current_node.m_rchild is None:
                        current_node.m_rchild = new_node
                        break
                    else:
                        current_node = current_node.m_rchild

    def delete(self, val):
        current_node = self.m_root
        parent_node = None
        # Search for the node to be deleted:
        while current_node and current_node.m_value != val:
            parent_node = current_node
            if val < current_node.m_value:
                current_node = current_node.m_lchild
            else:
                current_node = current_node.m_rchild
        # If node is not found:
        if not current_node:
            print(f"Node {val} is not in the Tree!")
            return
        # Case 1: Node with no child or 1 child
        if not current_node.m_lchild or not current_node.m_rchild:
            if current_node.m_lchild:
                child = current_node.m_lchild
            else:
                child = current_node.m_rchild
            if parent_node.m_lchild == current_node:
                parent_node.m_lchild = child
            else:
                parent_node.m_rchild = child
        # Case 2: Node with 2 children, find the smallest node in the right subtree means to find a node in right subtree which doesn't have a left subtree
        else:
            successor_parent = current_node
            successor = current_node.m_rchild
            while successor.m_lchild:
                successor_parent = successor
                successor = successor.m_lchild
            current_node.m_value = successor.m_value
            if successor_parent.m_lchild == successor:
                successor_parent.m_lchild = successor.m_rchild
            else:
                successor_parent.m_rchild = successor.m_rchild

    def search(self, val):
        current_node = self.m_root
        while True:
            if val == current_node.m_value:
                print(f"Node {val} is found!")
                break
            elif val < current_node.m_value:
                if current_node.m_lchild is None:
                    print(f"Node {val} is not in the tree!")
                    break
                else:
                    current_node = current_node.m_lchild
            else:
                if current_node.m_rchild is None:
                    print(f"Node {val} is not in the tree!")
                    break
                else:
                    current_node = current_node.m_rchild

    def preorder_visit(self):
        current_node = self.m_root
        preorder_list = []
        while current_node or preorder_list:
            while current_node:
                print(f"Preorder visit: {current_node.m_value}")
                preorder_list.append(current_node)
                current_node = current_node.m_lchild
            if preorder_list:
                current_node = preorder_list.pop()
                current_node = current_node.m_rchild

    def inorder_visit(self):
        current_node = self.m_root
        inorder_list = []
        while current_node or inorder_list:
            while current_node:
                inorder_list.append(current_node)
                current_node = current_node.m_lchild
            current_node = inorder_list.pop()
            print(f"In-order visit: {current_node.m_value}")
            current_node = current_node.m_rchild

    def postorder_visit(self):
        current_node = self.m_root
        visit_list = []
        last_visited = None
        while current_node or visit_list:
            while current_node:
                visit_list.append(current_node)
                current_node = current_node.m_lchild
            top_node = visit_list[-1]
            if top_node.m_rchild and last_visited != top_node.m_rchild:
                current_node = top_node.m_rchild
            else:
                visit_list.pop()
                print(f"Post-order visit: {top_node.m_value}")
                last_visited = top_node


bst = BST()
bst.insert(10)
bst.insert(8)
bst.insert(9)
bst.insert(15)
bst.insert(4)
bst.search(10)
bst.preorder_visit()
bst.inorder_visit()
bst.postorder_visit()
bst.delete(8)
print("Tree after deleting: ")
bst.inorder_visit()

```

```py
# Using recursion:
class BST:
    def __init__(self, root):
        self.m_root = root
        self.m_lchild = None
        self.m_rchild = None

    def insert(self, val):
        if self.m_root is None:
            self.m_root = val
            return
        if val < self.m_root:
            if self.m_lchild:
                self.m_lchild.insert(val)
            else:
                self.m_lchild = BST(val)
        else:
            if self.m_rchild:
                self.m_rchild.insert(val)
            else:
                self.m_rchild = BST(val)

    def delete(self, val):
        if self.m_root is None:
            print("The tree is empty!")
            return
        if val < self.m_root:
            if self.m_lchild:
                self.m_lchild = self.m_lchild.delete(val)
            else:
                print(f"Value {val} is not in the Tree!")
        elif val > self.m_root:
            if self.m_rchild:
                self.m_rchild = self.m_rchild.delete(val)
            else:
                print(f"Value {val} is not in the Tree!")
        else:
            # Case_1: Node with 1 child or no child
            if self.m_lchild is None:
                return self.m_rchild
            if self.m_rchild is None:
                return self.m_lchild
            # Case_2 Node with 2 child, find the smallest value in the right subtree, or find the largest value in the left subtree, here we follow the first principle
            replace_node = self.m_rchild
            while replace_node.m_lchild:
                replace_node = replace_node.m_lchild
            self.m_root = replace_node.m_root
            self.m_rchild = self.m_rchild.delete(replace_node.m_root)
        return self

    def search(self, val):
        if val == self.m_root:
            print(f"Node {val} is found!")
            return
        elif val < self.m_root:
            if self.m_lchild:
                self.m_lchild.search(val)
            else:
                print(f"Node {val} is not found in the tree!")
        else:
            if self.m_rchild:
                self.m_rchild.search(val)
            else:
                print(f"Node {val} is not found in the tree!")

    def preorder_visit(self):
        print(f"Preorder visit: {self.m_root}")
        if self.m_lchild:
            self.m_lchild.preorder_visit()
        if self.m_rchild:
            self.m_rchild.preorder_visit()

    def inorder_visit(self):
        if self.m_lchild:
            self.m_lchild.inorder_visit()
        print(f"In-order visit: {self.m_root}")
        if self.m_rchild:
            self.m_rchild.inorder_visit()

    def postorder_visit(self):
        if self.m_lchild:
            self.m_lchild.postorder_visit()
        if self.m_rchild:
            self.m_rchild.postorder_visit()
        print(f"Post-order visit: {self.m_root}")

bst = BST(10)
bst.insert(8)
bst.insert(9)
bst.insert(15)
bst.insert(4)
bst.search(10)
bst.preorder_visit()
bst.inorder_visit()
bst.postorder_visit()
bst.delete(8)
print("Tree after deleting: ")
bst.inorder_visit()

```
