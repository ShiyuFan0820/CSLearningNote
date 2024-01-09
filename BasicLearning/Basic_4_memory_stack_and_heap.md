# Memory Stack and Heap

When the program is running, data must be stored in memory temporaril. How much memory a piece of data requires, where it is stored, and how it is stored all depend on the type of data. The running program uses two memory regions to store data -- memory stack and memory heap.

## What is Memory Stack and How it Operates

Memory stack is one of the memory regions to store information temporarily when the program is running. Memory stack has two operations -- push and pop. Push is that when has a chains of function calls, a stack frame will be created for each function, the arguments and variables inside the stack must have it's size known at compile time and follow the rules of FILO (first in last out) or LIFO (last in first out). When a function returns, the stack frame will be popped off and end the function, all values will be destoryed, this means in stack the cleanup is automatic when the function returns the value. The size of the stack is daynamic but it has a fixed upper limit.

To show how memory stack operates there is an example: 


## What is Memory Heap and How it Operates

We already know that values and variables will be deleted when a function return values in memory stack, to prevent them to be deleted we need to store them in memory heap, values in heap will not be destoryed automatically, it's manually. And we also know that in stack frame, all values are follow the rules of FILO (first in last out) or LIFO (last in first out), this means we have to access the values in this particular order, so if we want to access values by multiple threads (call values anywhere in the program) we also need to store them in memory heap, it's more flexiable than memory stack.

## Stack Overflow

As mentioned before, the size of the stack has a fixed upper limit, this is defined when the program starts up. When we supass the limit in stack while running the program, we will get the stack overflow error. For example if we write a infinite recursive code, then memory stack could grow as the code executes, once we exhaust the limit, stack overflow will occur.

Something similar to stack overflow also happens in memory heap, it's called out of memory. Memory heap doesn't have a upper limit, but if you forget to delete the values manually, this part of memory could not be freed, causing memory leak, once you run out of the physical memory availalbe, the program could crash and stop.

## Memory Stack vs Memory Heap


