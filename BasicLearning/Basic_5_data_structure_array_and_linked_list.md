# Data Structure -- Array and Linked List

Array and linked list are both data structures used to store and organize elements, but they differ in their underlying implementations and performance characteristics.

## What is Array and How it Operates?

Array is List in Python, vector in C++, and ArrayList in Java. It is a contiguous block of memory heap where elements are stored, and can be access using an index or key. 

**Example**  

If we wanted to store a string of integers in an array, it would look like this in memory:

<div align=center>
<img width="600" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/79362cd4-db16-43da-af3b-0fd265c40d74">
</div>

Assuming that the address of the first element is 200, if we want to calculate the address of element at index i, and a size of an integer is typically 4, so the address of the element is equal to `200 + 4 * i`.

<div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/f6c265a1-e92f-42ba-9193-e570e3bc3eb9">
</div>

**Memory Allocation:**  

In array, memory is allocated statically or dynamically, the size of the array is fixed during declaration and can be resized during runtime if we want to add new element in the array. But because the memory allocated is a contiguous block, if the size of elements in array surpass the available contiguous memory, the out of memory error will occur.

**Access Time:**  

Elements in array can be accessed in constant time O(1)<sup>*note</sup> since elements are stored in contiguous block, we can randomly access the address of any element as long as we know the address of the head element.

_*note: Big O notation `O(n)` is Linear Time Complexity, `n` is the total input, the time complexity of an algorithm is directly proportional to the size of the input, as the input size grows, the time taken by the algorithm also grows linearly. For example, doubling the input size of an algorithm, would roughly double the time it takes to excute the algorithm._

**Insertion and Deletion:**  

1. When insert/delet an element at the beginning of an array.  

In this situation we need to shift each element by one position towards the higher index, so the time taken will be proportional to the size of the array, it is time O(n).

2. When insert/delete an element in the middle of an array.  

In this situation we also need to shift elements, the time is O(n).

3. When insert/delete an element at the end of an array.  

If there is space in the array, we just add the element to the next higher index of the array, so the time is O(1), if the array is full we have to create a new array and copy all the previous elements to the new array, the time is O(n).

**Simulate the Operations of Array and Write a Array Class in Python**
```py
class Array:
    def __init__(self):
        self.m_array = [None] * 4
        self.m_used_size = 0
        self.m_delete_idx = ""

    def add(self, val):
        if self.m_used_size >= len(self.m_array):
            new_array = [None] * (len(self.m_array) * 2)
            for index in range(len(self.m_array)):
                new_array[index] = self.m_array[index]
            self.m_array = new_array
        self.m_array[self.m_used_size] = val
        self.m_used_size += 1
        self.print_array()

"""
When I first wrote the delete method I wrote like this:
    def delete(self, idx):
        self.m_array[idx] = None
        self.m_used_size -= 1
        self.print_array()
        
The problem is:
I didn't shift all the elements after the index of input forward, this caused if I deleted the element which was not at the last position, the used size would be subtracted by 1, after that when I called the add method, the element at the last position would be replaced to the new element and the used size would be added by 1 and when I called size method and printed the new array, the elements printed would be one less than the used size reported by the size method.
"""
    def delete(self, idx):
        replace_idx = idx
        next_idx = idx + 1
        while self.m_array[replace_idx] is not None:
            self.m_array[replace_idx] = self.m_array[next_idx]
            replace_idx += 1
            next_idx += 1
        self.m_used_size -= 1
        self.print_array()

    def get(self, idx):
        get_ele = self.m_array[idx]
        print(f"The element of index {idx} is {get_ele}.")

    def replace(self, idx, val):
        self.m_array[idx] = val
        self.print_array()

    def size(self):
        print(f"The total size of the array is {len(self.m_array)}, the size being used now is {self.m_used_size}.")

    def print_array(self):
        array_result = ""
        for ele in self.m_array:
            if ele is not None:
                array_result += str(ele) + ","
        print(array_result)

```


## What is Linked List and How it Operates?

Linked List is List in C++, LinkedList in Java, python doesn't have Linked List. It's a data structure where elements are stored in discontinuous heap memory, each element is randomly stored in a node which contains a value part and a address part (or a pointer) to the next node.

**Example:**

The same example, if we wanted to store a string of integers in a Linked List, it would look like this in memory:

<div align=center>
<img width="600" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/0072d29e-6c50-4852-a6f9-d4d510d80b4c">
</div>

**Memory Allocation:**

Memory are allocated dynamically in Linked List and elements are stored in nodes, in this way programmer could take advantage of the scattered memory.

But Linked list could take up more memory than array because it needs to store an additional address to the next element.

**Access Time:**

Accessing elements in a linked list requires traversing the list from the beginning as the pointer in stack will only stores the head node, so the access time is O(n).

**Insertion and Deletion:**

1. When insert/delete an element at the beginning of a Linked List.  

Inserting an element at the beginning of the list means to creat a new node and adjust the link, the time is O(1).

2. When insert/delete an element in the middle of a Linked List.  

Inserting an element in the middle of the list means to traverse the list till that position and create a new node and adjust the link, the time complexity is O(n).

3. When insert/delete an element at the end of a Linked List.  

Inserting an element at the end of the list means to traverse the whole list and creat a new node and adjust the link, the time is O(n).

**Simulate the Operations of Linked List and Write a Linked List Class in Python**
```py
class Node:
    def __init__(self, val):
        self.m_value = val
        self.m_pointer = None


class LinkedList:
    def __init__(self):
        self.m_head = None

    def is_empty(self):
        return self.m_head

    def add(self, val):
        new_node = Node(val)
        if self.is_empty() is None:
            self.m_head = new_node
        else:
            current_node = self.m_head
            while current_node.m_pointer:
                current_node = current_node.m_pointer
            current_node.m_pointer = new_node
        print(f"Linked List after adding val {val}:")
        self.print_list()

    def delete_by_value(self, val):
        current_node = self.m_head
        if current_node.m_value == val:
            self.m_head = current_node.m_pointer
            print(f"Linked List after deleting value {val}:")
            self.print_list()
            return
        previous_node = None
        while current_node.m_value != val:
            if current_node.m_pointer is None:
                print(f"There is no value {val} in the list.")
                return
            else:
                previous_node = current_node
                current_node = current_node.m_pointer
        previous_node.m_pointer = current_node.m_pointer
        print(f"Linked List after deleting value {val}:")
        self.print_list()

    def delete_by_index(self, idx):
        idx_count = 0
        current_node = self.m_head
        if idx == idx_count:
            self.m_head = current_node.m_pointer
        previous_node = None
        while idx > idx_count:
            previous_node = current_node
            current_node = current_node.m_pointer
            idx_count += 1
        previous_node.m_pointer = current_node.m_pointer
        print(f"Linked List after deleting index {idx}:")
        self.print_list()

    def print_list(self):
        current_node = self.m_head
        while current_node:
            print(f"{current_node.m_value}, -->")
            current_node = current_node.m_pointer
        print("None\n")


linkedlist = LinkedList()
linkedlist.add(1)
linkedlist.add(2)
linkedlist.add(3)
linkedlist.delete_by_value(1)
linkedlist.delete_by_index(1)


# Run the code the output is:

Linked List after adding val 1:
1, -->
None

Linked List after adding val 2:
1, -->
2, -->
None

Linked List after adding val 3:
1, -->
2, -->
3, -->
None

Linked List after deleting value 1:
2, -->
3, -->
None

Linked List after deleting index 1:
2, -->
None
```

## Array vs Linked List

|Data Structure|Size Flexibility|Memory Allocation|Access Efficiency|Memory Usage|Insertion/Deletion|
|:--------------:|:-----------------:|:----------------:|:-----------------:|:-------------:|:-----------------:|
|Array | Size is known at compile time and can resize at runtime (resizing is expensive)| Require contiguous memory block | Accessing is efficient using index| Only stores contiguous data, could cause out of memory if there is no enough contiguous block to store data| Less efficient when insert in the beginning or middle position because it requires shifting elements |
|Linked List| Easy to grow by adding new nodes| Elements can be stored in scattered memory, linked by pointers|Accessing is inefficient as traversing from the element at the beginning| Additional memory for storing pointer in each node. | More efficient, just change the pointers if the node location is known |

