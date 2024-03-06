# Stack

## Introduction of Stack Data Structure

Stack data structure and memory stack which we have learned previously are related concept but operate at different levels. 

Memory stack is a memory area used for storing function call frames and local variables, when the function returns, the frames will be popped out of the stack, it follows the rule of LIFO (Last in first out), these operations are managed and implemented by the operating system and hardware, programmers usually don't interact with the memory stack in the code.

Stack data structure is an abstract data type (ADT), it's a linear data structure represents a collection of elements with the primary operations of push and pop, it also follow the rule of LIFO (Last in first out), insertion and deletion can only be performed at the end, i.e. at the top of the stack. Just like we have a stack of plates, we always put new plates on top, and when we take plates, we also start at the top. Stack data strucutre is explicitly managed by programmers, usually using arrays or linked lists to implement it.

<div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/6648b081-1417-434b-acc5-11546122c4a1">
</div>

## Operations of Stack

The commonly used operations of stack are push and pop.

Push is inserting an element to the top of the stack.

Pop is removing an element from the top of the stack.

Additionally, peak operation returns the top most element from the stack without removing it from the stack.

# Queue

## Introduction of Queue

Queue is also a linear data structure, but it follows the rule of FIFO (First in first out), there are 3 main types of queues, they are cicular queues, double-ended queues, and priority queues.

## Operations of Queue

There are two operations commonly used in queue -- enqueue and dequeue.

Enqueue operation adds a new element at the end of a queue, it's like a person join the end of a line or queue at a snack bar.

Dequeue operation removes the first element in a queue, it's like the first person in the queue get the snack and leave the queue.

Queue data structure can also be implemented by using arrays or linked lists.
