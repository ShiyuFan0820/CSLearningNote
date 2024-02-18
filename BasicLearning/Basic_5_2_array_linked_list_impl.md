**Array in Python**

The code is:
```py
class Array:
    def __init__(self):
        self.m_array = [None] * 4
        self.m_used_size = 0

    def add(self, val):
        if self.m_used_size >= len(self.m_array):
            new_array = [None] * (len(self.m_array) * 2)
            for index in range(len(self.m_array)):
                new_array[index] = self.m_array[index]
            self.m_array = new_array
        self.m_array[self.m_used_size] = val
        self.m_used_size += 1
        print(f"Array after adding {val}:")
        self.print_array()

    def delete_by_value(self, val):
        target_idx = 0
        while self.m_array[target_idx] != val:
            target_idx += 1
        replace_idx = target_idx
        next_idx = replace_idx + 1
        while self.m_array[replace_idx] is not None:
            self.m_array[replace_idx] = self.m_array[next_idx]
            replace_idx += 1
            next_idx += 1
        self.m_used_size -= 1
        print(f"Array after deleting by value {val}:")
        self.print_array()

    def delete_by_index(self, idx):
        """
         When I first wrote the delete code I wrote like this:
        self.m_array[idx] = None
        self.m_used_size -= 1
        self.print_array()

        The problem is:
        I didn't shift all the elements after the index of input forward, this caused if I deleted the element which was not at the last position, after that when I called the add method, the element at the last position would be replaced to the new element and the used size would add 1 and when I called size method and printed the new array, the elements printed would be one less than the used size reported by the size method.
        """
        replace_idx = idx
        next_idx = idx + 1
        while self.m_array[replace_idx] is not None:
            self.m_array[replace_idx] = self.m_array[next_idx]
            replace_idx += 1
            next_idx += 1
        self.m_used_size -= 1
        print(f"Array after deleting by index {idx}:")
        self.print_array()

    def get(self, idx):
        get_ele = self.m_array[idx]
        print(f"The element of index {idx} is {get_ele}.\n")

    def replace(self, idx, val):
        self.m_array[idx] = val
        print(f"Array after replacing value of index {idx} with {val}:")
        self.print_array()

    def size(self):
        print(f"The total size of the array is {len(self.m_array)}, the size being used now is {self.m_used_size}.\n")

    def print_array(self):
        array_result = ""
        for ele in self.m_array:
            if ele is not None:
                array_result += str(ele) + ","
        print(f"{array_result}\n")


if __name__ == "__main__":
    array = Array()
    array.add(1)
    array.add(2)
    array.add(3)
    array.get(0)
    array.replace(2, 4)
    array.size()
    array.delete_by_index(0)
    array.delete_by_value(4)

```

The output is:
```py
Array after adding 1:
1,

Array after adding 2:
1,2,

Array after adding 3:
1,2,3,

The element of index 0 is 1.

Array after replacing value of index 2 with 4:
1,2,4,

The total size of the array is 4, the size being used now is 3.

Array after deleting by index 0:
2,4,

Array after deleting by value 4:
2,
```

**Linked List in Python**

The code is:
```py
class Node:
    def __init__(self, val):
        self.m_value = val
        self.m_next = None


class LinkedList:
    def __init__(self):
        self.m_head = None

    def is_empty(self):
        return self.m_head

    def add(self, val):
        new_node = Node(val)
        if not self.is_empty():
            self.m_head = new_node
        else:
            current_node = self.m_head
            while current_node.m_next:
                current_node = current_node.m_next
            current_node.m_next = new_node
        print(f"Linked List after adding val {val}:")
        self.print_list()

    def delete_by_value(self, val):
        current_node = self.m_head
        if current_node.m_value == val:
            self.m_head = current_node.m_next
            print(f"Linked List after deleting value {val}:")
            self.print_list()
            return
        previous_node = None
        while current_node.m_value != val:
            if not current_node.m_next:
                print(f"There is no value {val} in the list.")
                return
            else:
                previous_node = current_node
                current_node = current_node.m_next
        previous_node.m_next = current_node.m_next
        print(f"Linked List after deleting value {val}:")
        self.print_list()

    def delete_by_index(self, idx):
        idx_count = 0
        current_node = self.m_head
        if idx == idx_count:
            self.m_head = current_node.m_next
        previous_node = None
        while idx > idx_count:
            previous_node = current_node
            current_node = current_node.m_next
            idx_count += 1
        previous_node.m_next = current_node.m_next
        print(f"Linked List after deleting index {idx}:")
        self.print_list()

    def print_list(self):
        current_node = self.m_head
        output = ""
        while current_node:
            output += f"{current_node.m_value}-->"
            current_node = current_node.m_next
        output += "None"
        print(output)


if __name__ == "__main__":
    linkedlist = LinkedList()
    linkedlist.add(1)
    linkedlist.add(2)
    linkedlist.add(3)
    linkedlist.delete_by_value(1)
    linkedlist.delete_by_index(1)

```

The output is:
```py
Linked List after adding val 1:
1-->None
Linked List after adding val 2:
1-->2-->None
Linked List after adding val 3:
1-->2-->3-->None
Linked List after deleting value 1:
2-->3-->None
Linked List after deleting index 1:
2-->None
```
