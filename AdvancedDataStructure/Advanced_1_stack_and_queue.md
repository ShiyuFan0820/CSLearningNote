# Stack

## Introduction of Stack in Data Structure

Stack in data structure and memory stack which we have learned previously are related concept but operate at different levels. 

Memory stack is a memory area used for storing function call frames and local variables, when the function returns, the frames will be popped out of the stack, it follows the rule of LIFO (Last in first out), these operations are managed and implemented by the operating system and hardware, programmers usually don't interact with the memory stack in the code.

Stack in data structure is an abstract data type (ADT, which defines a set of operations that can be performed on a data structure), it's a linear data structure represents a collection of elements with the primary operations of push and pop, it also follow the rule of LIFO (Last in first out), insertion and deletion can only be performed at the end, i.e. at the top of the stack. Just like we have a stack of plates, we always put new plates on top, and when we take plates, we also start at the top. Stack in data structure is explicitly managed by programmers, usually using arrays or linked lists to implement it.

<div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/6648b081-1417-434b-acc5-11546122c4a1">
</div>

Stack is widly used for expression evaluation, undo functionality, browser history, backtracking algorithms.

## Operations of Stack

The commonly used operations of stack are push and pop.

Push is inserting an element to the top of the stack.

Pop is removing an element from the top of the stack.

Additionally, peak operation returns the top most element from the stack without removing it from the stack.

# Queue

## Introduction of Queue

Queue is also an abstract data type, it's a linear data structure, but it follows the rule of FIFO (First in first out).

## Operations of Queue

Queue typically maintains two pointers -- a froint pointer(head) and a rear pointer(tail), these pointers keep track of where new elements should be added and removed.

There are two operations commonly used in queue -- enqueue and dequeue.

Enqueue operation adds a new element to the rear of a queue, it's like a person join the end of a line or queue at a snack bar.

Dequeue operation removes the element from the front of the queue, it's like the first person in the queue get the snack and leave the queue.

Queue data structure can also be implemented by using arrays or linked lists.

## Different Types of Queue

There are 3 main types of queues, they are circular queue, double-ended queus, and priority queue.

### Circular Queue

Circular queue also known as a ring buffer because the last elementis connect to the first element, is a variation of the queue data structure with a fixed-size capacity, meaning it can hold only a limited number of elements determined at the time of its creation. 

In a circular queue also maintains two pointers.

Enqueue operation add a new element at the position pointed to by the rear pointer, if the rear pointer reaches the end of the cicular queue, it wraps around to the beginning, allowing elements to be enqueued in a circular manner.

Dequeue operation removes an element from the position pointed to by the front pointer, if the front pointer reaches the end of the queue, it wraps around to the beginning.

When the front pointer and the rear pointer coincide, this indicates that the circular queue is empty.

**Example of circular queue** 

The rear pointer is already at the end of the queue in the circular queue above, if we want to enqueue another element `9` to the queue, just wrapping the rear pointer to the beginning of the queue like a ring_

<div align=center>
<img width="500" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/e4057b2a-8a12-4370-88a3-e35b95a562ca">
</div>

### Double-ended Queue/Deque

Double-ended queue is commonly abbreviated as deque, it supports insertion and deletion of elements from both ends.

Similar to standard queue, a deque maintains two pointers, Elements can be inserted or removed from both ends of the deque using operations such as `append` (to add an element to the rear), `appendleft` (to add an element to the front), `pop` (to remove an element from the rear), and `popleft` (to remove an element from the front).

### Priority Queue

Priority queue is a type of queue where elements are processed based on their priority rather than the order in which they were added. Elements in a priority queue must be comparable or associated with a comparable value which determines their relative importance, e.g. elements of small numbers have a higher priority or large numbers have a higher priority. Elements with higher priority are more urgent and are placed in the front of the queue, and are dequeued before elements with lower priority.

**Implementation of Priority Queue**

Priority queue is commonly implemented by using a heap data structure because this is a faster way to retrieve the desired element where the time complexity is O(log<sup>n</sup>), compared to O(n) by only using an array-based implementation.







