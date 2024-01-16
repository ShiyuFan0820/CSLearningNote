# Data Structure -- Array and Linked List

Array and linked list are both data structures used to store and organize elements, but they differ in their underlying implementations and performance characteristics.

## What is Array and How it Operates?

Array is List in Python, vector in C++, and ArrayList in Java. It is a contiguous block of memory heap where elements are stored, and can be access using an index or key. 

**Memory Allocation:**  
In array, memory is allocated statically or dynamically, the size of the array is fixed during declaration and can be resized during runtime if we want to add new element in the array. But because the memory allocated is a contiguous block, if the size of elements in array surpass the available contiguous memory, the out of memory error will occur.

**Access Time:**  
Elements in array can be accessed in constant time O(1)<sup>*note</sup> since elements are stored in contiguous block, we can randomly access the address of any element as long as we know the address of the head element.

_*note: Big O notation `O(n)` is Linear Time Complexity, `n` is the total input, the time complexity of an algorithm is directly proportional to the size of the input, as the input size grows, the time taken by the algorithm also grows linearly. For example, doubling the input size of an algorithm, would roughly double the time it takes to excute the algorithm._

**Insertion and Deletion:**  
1. When insert an element at the beginning of an array.  
In this situation we need to shift each element by one position towards the higher index, so the time taken will be proportional to the size of the array, it is time O(n).

2. When insert an element in the middle of an array.  
In this situation we also need to shift elements, the time is O(n).

3. When insert an element at the end of an array.  
If there is space in the array, we just add the element to the next higher index of the array, so the time is O(1), if the array is full we have to create a new array and copy all the previous elements to the new array, the time is O(n).

**Example**  
If we wanted to store a string of integers in an array, it would look like this in memory:

<div align=center>
<img width="600" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/79362cd4-db16-43da-af3b-0fd265c40d74">
</div>

Assuming that the address of the first element is 200, if we want to calculate the address of element at index i, and a size of an integer is typically 4, so the address of the element is equal to `200 + 4 * i`.

<div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/f6c265a1-e92f-42ba-9193-e570e3bc3eb9">
</div>

**Simulate the Operations of Array and Write a Array Class in Python**
```py
class Array:
    def __init__(self):
        self.m_array = [None] * 4
        self.used_size = 0
        self.count_idx = 0
        self.m_delete_idx = ""

    def add(self, val):
        if self.used_size >= len(self.m_array):
            new_array = [None] * (len(self.m_array) * 2)
            for index in range(len(self.m_array)):
                new_array[index] = self.m_array[index]
            self.m_array = new_array
        self.m_array[self.used_size] = val
        self.used_size += 1
        self.print_array()

"""
When I first wrote the delete method I wrote like this:
    def delete(self, idx):
        self.m_array[idx] = None
        self.m_size -= 1
        self.print_array()
        
The problem is:
I didn't shift all the elements after the index of input forward, this caused if I deleted the element which was not at the last position, after that when I called the add method, the element at the last position would be replace to the new element and the used size would add 1 and when I called size method and printed the new array, the elements printed would be one less than the used size reported by the size method.
"""
    def delete(self, idx): 
        replace_idx = idx
        next_idx = idx + 1
        while self.m_array[replace_idx] is not None:
            self.m_array[replace_idx] = self.m_array[next_idx]
            replace_idx += 1
            next_idx += 1
        self.used_size -= 1
        self.print_array()

    def get(self, idx):
        get_ele = self.m_array[idx]
        print(f"The element of index {idx} is {get_ele}.")

    def replace(self, idx, val):
        self.m_array[idx] = val
        self.print_array()

    def size(self):
        print(f"The total size of the array is {len(self.m_array)}, the size being used now is {self.used_size}.")

    def print_array(self):
        array_result = ""
        for ele in self.m_array:
            if ele is not None:
                array_result += str(ele) + ","
        print(array_result)

```


## What is Linked List and How it Operates?



## Array vs Linked List
