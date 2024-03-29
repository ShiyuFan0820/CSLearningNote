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

## What is Linked List and How it Operates?

Linked List is List in C++, LinkedList in Java, python doesn't have Linked List. It's a data structure where elements are stored in discontinuous heap memory, each element is randomly stored in a node which contains a value part and an address part (or a pointer) to the next node.

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

## Array vs Linked List

|Data Structure|Size Flexibility|Memory Allocation|Access Efficiency|Memory Usage|Insertion/Deletion|
|:--------------:|:-----------------:|:----------------:|:-----------------:|:-------------:|:-----------------:|
|Array | Size is known at compile time and can resize at runtime (resizing is expensive)| Require contiguous memory block | Accessing is efficient using index| Only stores contiguous data, could cause out of memory if there is no enough contiguous block to store data| Less efficient when insert in the beginning or middle position because it requires shifting elements |
|Linked List| Easy to grow by adding new nodes| Elements can be stored in scattered memory, linked by pointers|Accessing is inefficient as traversing from the element at the beginning| Additional memory for storing pointer in each node. | More efficient, just change the pointers if the node location is known |

