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

## Traversal Method in a Binary Search Tree

To traverse in a binary search tree, there are three visiting method -- pre-order, in-order and post-order. 

The visiting order of pre-order is that for each subtree firstly visit the root, then the left subtree, and lastly the right subtree, each node is visited before its children. This method is convenient for creating a copy of a tree.

The visiting order of in-order is a acsending order of their value, for each subtree it starts from the leftmost node (the one with the smallest value), then the root value and lastly goes to the rightmost node (the one with the largest value). This method is useful for retrieving elements in a tree where the order matters.

The visiting order of post-order is for each subtree, it starts from the left most node, then the rightmost node, lastly the root. This method is useful for freeing memory in a tree.

## Binary Search Tree Implementation in Python

To create a bianry search tree we can use iteration and recursion. The code below uses both ways to implement operations in a binary search tree.

_The code is:_
```py
# Using iteration:
class Nodes:
    def __init__(self, val):
        self.m_value = val
        self.m_lchild = None
        self.m_rchild = None


class Bst:
    def __init__(self):
        self.m_root = None

    def is_empty(self):
            return self.m_root is None

    def insert(self, val):
        new_node = Nodes(val)
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


bst = Bst()
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
# Using recursion 1:
class Bst:
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
                self.m_lchild = Bst(val)
        else:
            if self.m_rchild:
                self.m_rchild.insert(val)
            else:
                self.m_rchild = Bst(val)

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

bst = Bst(10)
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
# Using recursion 2:
class Node:
    def __init__(self, val):
        self.m_val = val
        self.m_left = None
        self.m_right = None

    def get_val(self):
        return self.m_val

    def get_right(self):
        return self.m_right

    def get_left(self):
        return self.m_left

    def set_right(self, right_val):
        self.m_right = right_val

    def set_left(self, left_val):
        self.m_left = left_val


class Bst:
    def __init__(self, root_val):
        self.m_root = Node(root_val)

    def insert(self, val):
        self.insert_to_node(self.m_root, val)

    def insert_to_node(self, node, val):
        if val < node.get_val():
            left_val = node.get_left()
            if left_val:
                self.insert_to_node(left_val, val)
            else:
                node.set_left(Node(val))
        else:
            right_val = node.get_right()
            if right_val:
                self.insert_to_node(right_val, val)
            else:
                node.set_right(Node(val))

    def find(self, val):
        self.find_in_node(self.m_root, val)

    def find_in_node(self, node, val):
        if val < node.get_val():
            if node.m_left:
                self.find_in_node(node.m_left, val)
            else:
                print(f"Value {val} doesn't exist!")
        elif val > node.get_val():
            if node.m_right:
                self.find_in_node(node.m_right, val)
            else:
                print(f"Value {val} doesn't exist!")
        else:
            print(f"Value {val} found!")

    def in_order(self, node):
        if node.m_left:
            self.in_order(node.m_left)
        print(f"Visiting: {node.get_val()}")
        if node.m_right:
            self.in_order(node.m_right)

    def print_inorder(self):
        print("--------In-order Visit--------")
        self.in_order(self.m_root)

    def pre_order(self, node):
        print(f"Visiting: {node.get_val()}")
        if node.m_left:
            self.pre_order(node.m_left)
        if node.m_right:
            self.pre_order(node.m_right)

    def print_preorder(self):
        print("--------Pre-order Visit--------")
        self.pre_order(self.m_root)

    def post_order(self, node):
        if node.m_left:
            self.post_order(node.m_left)
        if node.m_right:
            self.post_order(node.m_right)
        print(f"Visiting: {node.get_val()}")

    def print_postorder(self):
        print("--------Post-order Visit--------")
        self.post_order(self.m_root)


bst = Bst(10)
bst.insert(15)
bst.insert(8)
bst.insert(9)
bst.insert(5)
bst.insert(13)
bst.insert(20)

bst.find(10)
bst.find(8)
bst.find(6)
bst.print_inorder()
bst.print_preorder()
bst.print_postorder()

```

## Reconstruction of a Binary Tree

Reconstruciton of a binary tree is given two integer arrays preorder and inorder where preorder is the preorder traversal of a binary tree and inorder is the inorder traversal of the same tree, construct and return the bianry tree.

**Example:**

1. The given preorder and inorder arrays:
```py
preorder = [3, 9, 20, 15, 7]
inorder = [9, 3, 15, 20, 7]
```
2. According to the preorder array we can get the root node is `3`, and we can also know that numbers on the left side of the root is the elements of left subtree and numbers on the right side of the root is the elements of right subtree, so we can reconstruce the binary tree for the first step:

<div align=center>
<img width="411" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/5a262fa7-2f14-4b85-b418-e661d3f9454f">
</div>

3. According to the preorder array we can get the root of the right subtree is `20`, and according to the inorder array we can get the left subtree under root `20` is `15`, and right subtree under root `20` is `7`, we can complete the reconstruction of this binary tree:

<div align=center>
<img width="387" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/abc62bbd-a975-4aae-817a-ca4e0aea0e50">
</div>


## Self-balancing Bianry Search Tree and Rotations

**A Balanced Binary Search Tree**

A balanced binary search tree is in which the heights of subtrees of any node differ by at most 1， this means for any node, |Height(Left subtree) - Height(Right subtree)| <= 1, the tree remains balance by rotation, this property ensures that the tree remains symmetric and can perform efficient searching and other operations. There are two main types of self-balancing binary search tree -- AVL tree and Red Black tree.

**AVL Tree and Rotations**

An AVL tree is a self-balancing tree, it will rotate to remain balance everytime after inserton or deletion opertions. There are four types of imbalance in the AVL tree need to be rotated, they are LL (left-left) imbalance, LR (left-right) imbalance, RR (right-right) imbalance and RL (right-left) imbalance.

<div align=center>
<img width="800" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/d252a8a3-4407-4afe-825f-787c017d8165">
</div>

_How to balance an AVL tree:_

1. LL (left-left) imbalance. This is the left subtree of the node is taller than the right subtree of the node, and the left child's left subtree is taller than its right subtree. In this situation we need to do right rotation.

<div align=center>
<img width="800" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/26d311f3-e032-4860-a7bd-3b60764b0b03">
</div>

Balance step 1: Find the first node which is not balanced. Both node `7` and node `10` violate the rule of balance, we need to find the first imbalanced node from the bottom up, so node `7` is the first node.

Blance step 2: From node `7` down, find the two connected nodes, all rotation happens within 3 nodes. Rotate node `3` as the left child of the root `10`, node `7` as the right child of node `3`.

2. LR (left-right) imbalance. This the left subtree of the node is taller than the right subtree of the node, and the left child's right subtree is taller than its left subtree.

<div align=center>
<img width="900" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/d7c4d3ac-b133-49fd-9360-84abdd03bef8">
</div>

Balance step 1: Same with the instructon above.

Balance step 2: Rotate the right node `5` to the left subtree of node `7`, then the imbalanced tree became a LL imbalance, then follow the instruction as the LL imbalance to let the tree to be balanced.

3. RR (right-right) imbalance. This is the right subtree of the node is taller than left subtree of the node, and the right child's right subtree is taller than its left subtree.

<div align=center>
<img width="800" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/39aa4bfd-a8d3-4b31-848d-361653ae922d">
</div>

Balance step 1: Same with the instruction above.

Balance step 2: Rotate node `25` as the right child of the root `10`, rotate node `15` as the left child of the node `25`.

4. RL (right-left) imbalance. This is the right subtree of the node is taller than left subtree of the nodem and the right child's left subtree is taller than its right subtree.

<div align=center>
<img width="900" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/8d6e279a-6262-40d2-abaf-ccb6c678f0df">
</div>

Balance step 1: Same with the instructon above.

Balance step 2: Rotate the left node `20` to the right subtree of node `15`, then the imbalanced tree became a RR imbalance, then follow the instruction as the RR imbalance to let the tree to be balanced.

**Red-Black Tree**

Red-Black tree is a self-balancing tree, it contains properties like these below:

1. All nodes in the tree is either red or black, there will be an extra bit to store the color.
2. The root of the tree must be black.
3. The children of a red node must be black, this also means two red nodes can not be connected.
4. The node which doesn't have child will have the nil(=none) node as its child, and nil nodes are all black, nil nodes only serve the purpose for counting.
5. All paths from any node to its descendant nil node or leaf node contains the same number of black nodes(not counting the node itself), knowing as the black height.
6. The longest black height is at most twice the shortest black height.

A valid Red-Black tree:

<div align=center>
<img width="655" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/cd846d21-ba52-4118-a8f9-2b8f8fb9d841">
</div>

_How to balance a Red-Black tree:_

1. When insert a node in a Red-Black tree we follow the rules of inserting a node in a binary search tree. When insert a node, if the root is empty, the inserted node will be the root and the color will be black, if the root is not empty, the inserted node's color will be red.
2. Check if the parent of the inserted node is red, if the parent of the inserted node is red, this violates the rule of a Red-Black tree, then we need to check if the sibling of this parent (the node at the same depth of this parent node) is existing and check if it's red.
3. If the sibling node is red, see the sibling node, this parent node and their parent node as a triangle, if their parent node is not the root node, change the colors of all three nodes in the triangle to opposite colors, if their parent node is root node, just change the colors of the two nodes.
4. If the sibling node is black, we see the inserted node, the parent node and the parent of the parent node as a group, and regroup them into a triangle. Take the node with the median value among the three node as the root of this new triangle, change its color to black, change the left two nodes' color to red. The original left child of the node that becomes the root of the new triangle is moved to the left subtree and the right child is moved to the right subtree.
5. Repeat the step above till it follows the rules of a Red-Black tree.

_Example:_

When insert a node `28` in a Red-Black tree:

<div align=center>
<img width="650" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/99bc233a-2777-4e2b-b357-28ce73b2c571">
</div>

Check if the sibling of the parent node of the inserted node is existing and check if it's red. In this situation the sibling is existing and it's red. Find the little triangle.

<div align=center>
<img width="580" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/85470b0b-c2cb-4376-a162-506c8630d013">
</div>

Opposite the colors of the nodes in this triangle.

<div align=center>
<img width="650" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/47fe951e-5ba0-499c-bf5f-33ab7f657ac5">
</div>

It still violates the rule of a Red-Black tree. Now node `10` is the sibling node of node `30`, and it's black. See node `26`, node `30` and node `20` as a group.

<div align=center>
<img width="650" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/954aaa30-ed90-41d8-adf6-9e46682fb683">
</div>

Take the node with the median value among the three node as the root of this new triangle, in this case it's node `26`, change the color of node `26` into black and change the color of node `20` and node `30` into red, the original left child of the node `26` which is node `25` is moved to the left subtree and the right child which is the node `27` is moved to the right subtree. This way the tree became balance.

<div align=center>
<img width="650" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/eb62f203-9e02-42c8-9055-b7dcbe9fe594">
</div>




