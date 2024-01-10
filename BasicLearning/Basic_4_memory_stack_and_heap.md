# Memory Stack and Heap

When the program is running, data must be stored in memory temporarily. How much memory a piece of data requires, where it is stored, and how it is stored all depend on the type of data. The running program uses two memory regions to store data -- memory stack and memory heap.

## What is Memory Stack and How it Operates

Memory stack is one of the memory regions to store information temporarily when the program is running. Memory stack has two operations -- push and pop. Push is that when has a chains of function calls, a stack frame will be created for each function, the arguments and variables inside the stack must have it's size known at compile time and follow the rules of FILO (first in last out) or LIFO (last in first out). When reaches the end of the function, the stack frame will be popped out, the function will be end and return the values, all variables will be destoryed, this means in stack the cleanup is automatic when the function returns the value. The size of the stack is daynamic but it has a fixed upper limit.

**Example of  FILO (first in last out) or LIFO (last in first out):**

When we define 3 variables, they will be pushed into a memory stack, the first variable defined will be at the bottom of the stack.

_The defined variables:_
```c
a = 1
b = 2
c = 3
```
_Push them into a memory stack:_

<div align=center>
<img width="420" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/1d7901b1-8524-481d-aac6-ac9491e38ed8">
</div>

_Popped out when values returned, the last one pushed, the first one out:_

<div align=center>
<img width="420" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/ca163a3d-f8a7-40da-952f-a0824a54529c">
</div>

**To show how memory stack operates here is an example (C++):** 
```c
#include<stdio.h>

int Multiply(int n1, int n2)
{
  return n1*n2;
}

int main()
{
  int x = 2;
  int y = 3;
  int m = Multiply(x, y);
  printf("%d", m);
  return 0;
}
```
Push status:

_When the program starts executing the `main` method will always be invoked first, some memory from the stack will be allocated to it, also the local variables inside the main block will get some amount of memory according to their data type, this memory areas is called stack frame, when the `main` calls `m` which is equal to `Multiply` method, the stack frame for the function `Multiply` gets created:_

<div align=center>
<img width="250" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/a9cf4cd4-d04b-4373-aa63-68fabd23bc11">
</div>

Pop status:

_When the function `Multiply` reaches the end of the code, the function `Multiply` will get poped out of the stack and return a value, and similarly when it reaches the end of the `main` block, it will also get popped out from the stack and the console will print the returned value `6`:_

<div align=center>
<img width="700" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/ae4c7dde-fd62-48ad-ac94-77e8d3e25e76">
</div>

<div align=center>
<img width="700" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/156e3888-1060-4737-9827-4f81cb37ad15">
</div>

## What is Memory Heap and How it Operates

We already know that arguments and variables will be deleted when a function return values in memory stack, to prevent them to be deleted we need to store them in memory heap, arguments and variables in heap will not be destoryed automatically, it's manually, the lifetime of the data in memory heap is determined by the programmer. And we also know that in stack frame, all arguments and variables are follow the rules of FILO (first in last out) or LIFO (last in first out), this means we have to access them in this particular order we can't access them anywhere during the runtime, so if we want to access arguments and variables by multiple threads, we also need to store them in memory heap, it's more flexiable than memory stack. And it's size is not fixed, it can vary during the runtime of a program.

Memory heap has two operators, which are `new` and `delete`. When we want to create a variable and to store it in the memory heap, we use the keyword `new`, the memory will be allocated on the heap to store the variables and a pointer will point to the address on the heap, the address is randomly allocated, we can ask as many memories as we want as long as we don't run out of the memory on the system itself. The data will not be cleaned up untill we call the keyword `delete`.

**To show how memory heap operates here is an example (C++):** 
```c
#include <iostream>

int main() {
    
    int a = 5;
    
    std::cout << "a:"<<a<<std::endl;

    int *hp = new int(3);
    std::cout << "hp heap memory address:"<<hp<<std::endl;
    std::cout << "hp heap value:"<<*hp<<std::endl;

    int *ht = new int(4);
    std::cout << "ht heap memory address:"<<ht<<std::endl;
    std::cout << "ht heap value:"<<*ht<<std::endl;

    delete hp;
    std::cout << "hp heap memory address:"<<hp<<std::endl;
    std::cout << "hp heap value:"<<*hp<<std::endl;

    delete ht;
    std::cout << "ht heap memory address:"<<ht<<std::endl;
    std::cout << "ht heap value:"<<*ht<<std::endl;

    return 0;
}
```
"new" status:

_When invoke the `main` method, the integer `a` will be stored on the memory stack, when call `new` to allocate a memory to `hp` on heap, a pointer will point to a random address on the heap, which is the same for `ht`:_

<div align=center>
<img width="700" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/779554ab-ac9d-4931-9fa6-e9a55c873a4e">
</div>

_If we don't call the `delete`, the data will not be deleted on the heap:_

<div align=center>
<img width="700" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/c2dfb406-32b7-4f98-8e10-731442afa96d">
</div>

"delete" status:

_Once the `delete` is called the `ht` and `hp` will be destoryed, the memories pointed by the pointers will be deallocated, when you access the address again the value in the address is random:_

<div align=center>
<img width="700" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/ba80ba4f-385b-4444-823b-654acf81f42a">
</div>




## Stack Overflow

As mentioned before, the size of the stack has a fixed upper limit, this is defined when the program starts up. When we supass the limit in stack while running the program, we will get the stack overflow error. For example if we write a infinite recursive code, then memory stack could grow as the code executes, once we exhaust the limit, stack overflow will occur.

Something similar to stack overflow also happens in memory heap, it's called out of memory. Memory heap doesn't have a upper limit, but if you forget to delete the arguments and variables manually, this part of memory could not be freed, causing memory leak, once you run out of the physical memory availalbe, the program could crash and stop.

## Memory Stack vs Memory Heap


