**Python**
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
