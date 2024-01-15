# Data Structure -- Array and Linked List

Array and linked list are both data structures used to store and organize elements, but they differ in their underlying implementations and performance characteristics.

## What is Array and How it Operates?

Array is List in Python, vector in C++, and ArrayList in Java. It is a contiguous block of memory heap where elements are stored, and can be access using an index or key. 

**Memory Allocation:**  
In array, memory is allocated statically or dynamically, the size of the array is fixed during declaration and can be resized during runtime if we want to add new element in the array when the memory in array has run out.

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

**For Example:**  
If we wanted to store a string of integers in an array, it would look like this in memory:

<div align=center>
<img width="600" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/79362cd4-db16-43da-af3b-0fd265c40d74">
</div>

Assuming that the address of the first element is 200, if we want to calculate the address of element at index i, and a size of an integer is typically 4, so the address of the element is equal to `200 + 4 * i`.

<div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/f6c265a1-e92f-42ba-9193-e570e3bc3eb9">
</div>




## What is Linked List and How it Operates?



## Array vs Linked List