# Python Specific Properties

## Python List vs Tuple

**Python List**

Lists in python are like arrays in other programming language like C, C++ and Java, but more flexible. Lists are ordered collections of objects enclosed be square brackets and separated by commas, objects in lists can be arbitrary mixture of elements like numbers, strings or a nested list and so on. All elements in lists can be access by indexing, lists can be shrunk or grow, they are mutable.

Examples of lists:
```py
# An empty list:
empty_list = []

# A list of numbers:
num_list = [1, 2, 3, 4]

# A list of strings:
str_list = ["one", "two", "three", "four"]

# A list of mixture of numbers and strings:
mix_list = [1, 2, "one", "two"]

# A list of nested list:
nested_list = [1, 2, 3, 4, ["one", "two", "three", "four"]]
```

**Tuple**

Tuples' operations are similar to lists, but tuples are immutable, appending or removing elements in tuples are not allowed, and elements in tuples are enclosed in parentheses instead of square brackets.

Examples of tuples:
```py
# An empty tuple:
empty_tule = ()

# A tuple of numbers:
num_tuple = (1, 2, 3, 4)

# A tuple of strings:
str_tuple = ("one", "two", "three", "four")

# A tuple of mixture of numbers and strings:
mix_tuple = (1, 2, "one", "two")

# A tuple of nested tuple:
nested_tuple = (1, 2, 3, 4, ("one", "two", "three", "four"))
```

**Python List vs Tuple**

1. Lists are mutable and more versatile and suitable for scenarios where you need dynamic, mutable sequences of elements that can be modified or extended over time.
2. Tuples are immutable, since tuples are immutable, Python can optimize memory usage and execution speed.
3. Tuples are generally faster than lists, especially for operations like iteration and indexing.
4. Tuples can be used to return multiple values from a function.
5. Tuples can be used as dictionary keys as its immutable property.

## Shallow and Deep Copy

Shallow copy and deep copy are two ways to create copies of objects, such as lists, dictionaries, or custom objects. The difference lies in how nested objects are handled during the copying process.

**Shallow Copy**

1. Shallow copy can be performed using the `copy()` method or the `copy` module's `copy()` function.
2. A shallow copy creates a new object, but it doesn't create copies of nested objects within the orginal object, instead, it copies references to the nested objects. As a result, changes made to the nested objects in the copied object will also affect the original object, and vice versa.

**Deep Copy**

1. Deep copy can be performed using the `copy` module's `deepcopy()` function.
2. A deep copy creates a new object and recursively copies all nested objects within the original object. This means that changes made to the nested objects in the copied object will not affect the original object and vice versa.

**Attention**

Assignment is not a copying operation, instead it creates a new reference to the same object, this object just has two different variable names. To create a copy of an object that can be modified independently of the original, we should use like shallow copy ot deep copy mentioned above.

**Example**
```py
from copy import deepcopy

list_1 = [1, 2, 3, 4, [5, 6, 7]]
assignment = list_1
print(f"Assignment of list 1: {assignment}")
shallow_copy = list_1.copy()
print(f"A shallow copy of list 1: {shallow_copy}")
deep_copy = deepcopy(list_1)
print(f"A deep copy of list 1: {deep_copy}")

list_1[0] = "modified"
list_1[4][2] = "modified"

print("\n------Modify List 1------")

print(f"\nList 1 after modification: {list_1}")
print(f"Assignment after modification: {assignment}")
print(f"Shallow copy after modification: {shallow_copy}")
print(f"Deep copy after modification: {deep_copy}")
```

The output is:
```py
Assignment of list 1: [1, 2, 3, 4, [5, 6, 7]]
A shallow copy of list 1: [1, 2, 3, 4, [5, 6, 7]]
A deep copy of list 1: [1, 2, 3, 4, [5, 6, 7]]

------Modify List 1------

List 1 after modification: ['modified', 2, 3, 4, [5, 6, 'modified']]
Assignment after modification: ['modified', 2, 3, 4, [5, 6, 'modified']]
Shallow copy after modification: [1, 2, 3, 4, [5, 6, 'modified']]
Deep copy after modification: [1, 2, 3, 4, [5, 6, 7]]
```

## Set

A set is a collection of unique elements of any immutable data type(this means an element in a set can not be a list or other mutable data types) enclosed witnin curly brackets. They are like dictionaries without values. Here are some key properties of sets in Python:
1. Sets can't contain mutable objects.
2. Sets are mutable, this means we can add or remove elements in a set.
3. Sets don't allow duplicate elements, the operation of adding a duplicate element to a set will be ignored.
4. Sets are unordered collections, therefore, sets don't support indexing or slicing.

**Set operations**

[Check set operations in this website.](https://python-course.eu/python-tutorial/sets-and-frozen-sets.php)

## print Function

The print function in python is like this:
```py
print(value1, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
```

**"sep" in print Function**

We already know that when we want to print two elements by calling the print function, we write like this:
```py
print("a", "b")
```

The output would be:
```py
a b
```

The two elements are separated by comma in the print function and are separated by a space in the output, it's possible to redefine the seperator between elements by assigning an arbitrary string to the keyword parameter "sep":
```py
print("a","b",sep="")

print(192,168,178,42,sep=".")

print("a","b",sep=":-)")
```

The output is:
```py
ab

192.168.178.42

a:-)b
```

**"end" in print Function**

If we don't call the "end" parameter, the print call will be ended by a newline by defualt, we can assign an arbitrary string to the keyword parameter "end" to change the end behaviour:
```py
for i in range(4):
     print(i, end=" :-) ") 
```

The output is:
```py
0 :-) 1 :-) 2 :-) 3 :-)
```

**"file" in print Function**

If we don't call the "file" parameter, the output of the print function is send to the standard output stream (sys.stdout) by default, we can send the output into a different stream by redefining the keyword parameter "file":
```py
fh = open("data.txt","w")
print("42 is the answer, but what is the question?", file=fh)
fh.close()
```

The output will not be printed in the interactive shell, the output is sent to the file "data.txt".

## Pickle Module

Pickle is a module in Python which can serialize and de-serialize Python object structures, this means convert a Python object hierarychy into a byte stream, unpickle is the inverse operation. 

To achive this, we use the `pickle.dump()` method of the pickle mudule to convert the object into byte stream, and reread into a program by using the method `pickle.load(file)`.

**Example of How to Use Pickle Module in Python**

Convert an object into byte stream to a file:
```py
import pickle # Firstly, import the pickle module
cities = ["Paris", "Dijon", "Lyon", "Strasbourg"]
fh = open("data.pkl", "bw") # Open a file as binary write
pickle.dump(cities, fh) # Pickle the data using dump method
fh.close()
```

Reread the file data:
```py
import pickle
f = open("data.pkl", "rb")
villes = pickle.load(f)
print(villes)
```

_The output:_
```py
['Paris', 'Dijon', 'Lyon', 'Strasbourg']
```

## Shelve Module

The `pickle` module can only pickle one object at the time, while `shelve` module can deal with data object like dictionary. The values in a shelf can be arbitrary Python objects, the keys have to be strings.

**Example of How to Use Shelve Module**

Write objects into a shelf:
```py
import shelve # Firstly, import the shelve module.
s = shelve.open("MyShelve") # Open a shelve object with the shelve method open, if the file "MyShelve" already exists, the open method will try to open it. If it isn't a shelf file, we will get an error message. If the file doesn't exist, it will be created.

s["street"] = "Fleet Str" # Write object in the shelf, the operation is like those in a dictionary.
s["city"] = "London"
s.close() 
```

Read the objects in a shelf:
```py
import shelve
s = shelve.open("MyShelve")
print(s["street"])
print(s["city"])
```

_The output is:_
```py
Fleet Str
London
```

## lambda Function and map() Function

**lambda Function**

The lambda function or lambda operator is a way to create functions without a name.

The syntax of a lambda function: `lambda argument_list: expression`.

_Example of How to Use lambda:_
```py
# If we want to define a lambda function to return the sum of two arguments:
sum = lambda x, y : x + y

# Example test:
sum(1, 2)
```

_The output is:_
```py
3
```

**map() Function**

The `map()` function is a built-in function used to apply a specified function to each item in an iterable(such as a list, tuple, or string) and returns a new iterable containing the results. It takes two arguments: the function to apply and the iterable to apply it to.

_Example of How to Use map() function:_
```py
# A square function
def square(x):
     return x ** 2

# A list of numbers
numbers = [1, 2, 3, 4, 5]

# Usage of map() function
squared_nums_list = list(map(square, numbers))
print(squared_nums_list)
```

_The output is:_
```py
[1, 4, 9, 16, 25]
```

**Use map() Function with lambda Function**

We can define a funciton using lambda and apply it in a map function.

_Example of How to Use the Two Functions:_
```py
nums = [1, 2, 3, 4, 5]
squared_nums_list = list(map(lambda x: x ** 2, nums))
print(squared_nums_list)
```

_The output is:_
```py
[1, 4, 9, 16, 25]
```

Combine two functions making the syntax simpler.

## zip

Like the zipper of pants, when we zip the pants, the corresponding gear pairs snap together.

The `zip()` function in Python takes iterables(such as list, tuples, or strings) as input and returns an iterator that generates tuples containing elements from each iterable at the same index. If the input iterables are of different lengths, the iterator stops when the shortest iterable is exhausted.

_Example of How to Use zip() Function in Python:_
```py
# When two iterables have the same length
list1 = [1, 2, 3]
list2 = ['a', 'b', 'c']

for item in zip(list1, list2):
     print(item)

# When two iterables have different length
list1 = [1, 2, 3]
list2 = ['a', 'b']

for item in zip(list1, list2):
     print(item)
```

_The output is:_
```py
(1, 'a')
(2, 'b')
(3, 'c')

(1, 'a')
(2, 'b')
```

## Generator

The generator in Python looks like a function which returns a generator object, e.g. object can be iterated on, the difference is that generator object can generate one value at one time (also called lazily evaluation), rather than generating and storing all values at once like what for loop and while loop do, it essentially turns an iterable (An iterable is any object that can be iterated over, meaning it can be used in a loop, like lists, strings, tuples and dictionaries) into an iterator (An iterator is an object that represents a stream of data. It implements the iterator protocol, which requires methods like `__iter__()` and `__next__()`).

Generator can be defined by using generator function or generator expression. 

**Generator Function**

Defining a generator function is like defining a normal function, but it uses `yield` rather than `return`, a generator function works like this:
1. When we call a generator function, it returns a generator object without actually executing the body of the function.
2. We need to call `next()` keyword to start iterating the values of the genertor, the generator starts executing till the `yield` statement is reached, and return the value next to the `yield`. The execution will stop here.
3. As soon as we call `next()` again, it resume execution right after the `yield` statement where the last call was made, it will stop executing when the `yield` statement is reached again, the values of all variables remain the same with the previous call and ready for the following operations.
4. There can be more than one `yield` statement in a generator function, but when all values are already iterated through or there is a `return` statement in the code, it will raise `StopIteration` error. 

_Example of How a Generator Function Works: Let's illustrate how a generator works by writing a fibonacci generator function._

The code is:
```py
def fib(n):
    counter = 0
    n1 = 0
    n2 = 1
    while counter < n:
        print("Before yielding:") # We use two print lines to show how yield statement in a generator function works.
        yield n1
        print("Yielding passed.")
        n = n1 + n2
        n1 = n2
        n2 = n
        counter += 1
```

When we want to create the generator we call the generator function, and we print the object we can see in the console it returns a generator object:
```py
fib_gen = fib(3)
print(fib_gen)

"""
The output is:
<generator object fib at 0x100db0e40>
"""
```

Then we use one `next()` to start iterating the values, the generator will only return one value next to the `yield` at one time, and stop at the `yield` statement:
```py
num1 = next(fib_gen)
print(num1)

"""
The output is:
Before yielding:
0
"""
```

Then we call `next()` again, it starts executing right after the `yield` statement and stops till it reaches `yield` again, the values of all variables maintain the same with the previous call:
```py
num2 = next(fib_gen)
print(num2)

"""
The output is:
Yielding passed
Before yielding:
1
"""
```

Then we call `next()` twice, as it already iterated through all elements, the `StopIteration` error will be raised if `yield` statement is reached at forth time:
```py
num3 = next(fib_gen)
print(num3)

num4 = next(fib_gen)
print(num4)

"""
The output is:
Yielding passed
Before yielding:
1
Yielding passed

    num4 = next(fib_gen)
           ^^^^^^^^^^^^^
StopIteration
"""
```

**Generator Expression**

A generator expression is a concise way to create generator in Python, it's similar to list comprehension, but it uses parentheses `()` rather than square brackets `[]`.

_Example of How to A Generator Expression Works:_
```py
# Generator expression to generate squares of numbers from 1 to 5
squares_generator = (x ** 2 for x in range(1, 6))

# Call next() to get the iterate the values
print(next(squares_generator))
print(next(squares_generator))
print(next(squares_generator))
print(next(squares_generator))
print(next(squares_generator))

# Or we can use for loop to iterate over the squares
for square in squares_generator:
    print(square)

"""
The output is:
1
4
9
16
25
"""
```

**What are the Benefits of Using Generators?**

1. More readable: Generator is more readable rather than defining an empty list, appending and returning the result.
2. Memory efficiency: Generator generates one value at a time instead of generating and storing them all at once.
3. Lazy evaluation: Generator generate values as needed, reducing unnecessary computing.
4. There are other methods in generator like `send()`, `throw()` and `yield from`, [check this website for more detials](https://python-course.eu/advanced-python/generators-and-iterators.php).

## Decorator

**Definition of a Decorator in Python**

A decorator in Python is a function that takes an other function as an argument, adds some functionalities to the function and returns the modified/decorated function.

**Before Starting to Write the First Decorator Code**

To demonstrate how a decorator actually works, we first look at an outer function with a inner function in it:
```py
def out_func(msg):
    message = msg
    def inner_func():
        print(message)
    return inner_func()

out_func("Hi")

"""
The output is:
Hi
"""
```

When we use argument of `out_func` directly in `inner_func`, we can see the argument of `out_func` can be accessed in `inner_func`:
```py
def out_func(msg):
    def inner_func():
        print(msg)
    return inner_func()

out_func("Hi")

"""
The output is:
Hi
"""
```

If we delete the parentheses when returning the `inner_func`, the `inner_func` will be returned and assigned to the `call_func` variable which we defined, and then we can call the `call_func` to get the message printed:
```py
def out_func(msg):
    def inner_func():
        print(msg)
    return inner_func

call_func = out_func("Hi")
call_func()

"""
The output is:
Hi
```

Now we pass a function `message` as an argument to the `decorator_func`, and define a inner function call `wrapper_func` in it. Without modifying the `message` function, we can add any code in the `wrapper_func` to add some functionalities to the `message` function, here we add a print. Then when we call `decorator_func` and assign the returned value to the `decorated_message`, the `wrapper_func` is assigned to the `decorated_message`, and when we call `decorated_message` we get the printed output, and we can change the name of `decorated_message` to `message` because of the variable name just a reference to the function, the output is the same, this operation is like we decorate the `message` function and get a new `message` function:
```py
def decorator_func(original_func):
    def wrapper_func():
        print(f"Function wrapper executed before function {original_func.__name__}.")
        return original_func()
    return wrapper_func


def message():
    print("Function message called.")

# Change the decorated_message to message:
message = decorator_func(message)
message()

"""
The output is:
Function wrapper executed before function message.
Function message called.
"""
```

**How to Write a Decorator**

The decorator function in last example above is how a decorator work in Python, but Python has its own rules about how to write a decorator. 

In Python, decorators are typically written using a special syntax using the `@` symbol followed by the decorator function name, placed above the function definition, when we call the function, it will be passed in the decorator automatically. We can rewrite the example above like thie:
```py
def decorator_func(original_func):
    def wrapper_func():
        print(f"Function wrapper executed before function {original_func.__name__}.")
        return original_func()
    return wrapper_func

@decorator_func
def message():
    print("Function message called.")

message()

"""
The output is:
Function wrapper executed before function message.
Function message called.
"""
```

**Why a Decorator is Needed?**

Think about the Fibonacci function we defined before. When we want to query the n<sup>th</sup> number, we have to call the function every time to deduce from 1 to n. If we record the number everytime we call the function, we can get the n<sup>th</sup> number faster next time. 

We already know that a decorator can add some functionalities to a function, we can write a memoization decorator and apply it to the Fibonacci function to record the number every time we call it, this will aviod unnecessary calculation in the Fibonacci function if we call the function with the same argument, we can check the time efficiency of the function with and without a decorator, the code is:
```py
import time
def memorize_fib(fib):
    cache = {}
    def wrapper(n):
        if n not in cache:
            cache[n] = fib(n)
        return cache[n]
    return wrapper


@memorize_fib
def fib_with_memo(n):
    if n == 1:
        return 0
    elif n == 2:
        return 1
    else:
        return fib_with_memo(n - 1) + fib_with_memo(n - 2)


def fib_without_memo(n):
    if n == 1:
        return 0
    elif n == 2:
        return 1
    else:
        return fib_without_memo(n - 1) + fib_without_memo(n - 2)


star_time1 = time.time()
fib_with_memo(10)
end_time1 = time.time()
print(f"Execution time with memorize: {end_time1 - star_time1}.")

star_time2 = time.time()
fib_without_memo(10)
end_time2 = time.time()
print(f"Execution time without memorize: {end_time1 - star_time1}.")
```

When pass the `n = 50` to the two Fibonacci functions, it only returns the time of the function with memorize, the time fo the `fib_without_memo` is still executing and I haven't received the time of it:( :
```py
Execution time with memorize: 0.0001990795135498047.
```

<div align=center>
<img width="500" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/7f1303ee-45ff-4982-b428-558f0295c64c">
</div>

In summary, decorators in Python serve several important purposes:
1. Decorators allow to encapsulate functionality that can be applied to multiple functions or methods. Instead of duplicating code across different parts of your program, we can define the common functionality once and apply it using decorators.
2. Decorators provide a way to enhance or modify the behavior of functions or methods without changing their code directly. This is especially useful for extending the functionality of third-party libraries or built-in functions.


## List Comprehension

List comprehensions provide a concise way to create lists. They generate lists by applying an expression to each item an iterable(lists, tuples or strings) and filtering the items based on the condition. The syntax is:
```py
# List comprehension
new_list = [expression for item in iterable if condition]
```

**Example**

Assuming there is a list `nums = [1, 2, 3, 4, 5]`, using list comprehension to create a new list in which all elements are greater than `3`, and convert all integers to strings. The code is:
```py
nums = [1, 2, 3, 4, 5]
string_list = [str(num) for num in nums if num > 3]
print(string_list)

"""
The output is:
['4', '5']
```

In the example above, we want to create a new list based on the orginal list `nums`, so we need to loop through all elements in the `nums`, the expression is `str(num)`, it applies to each element in the new list, it's written before the for loop, the condition is `num > 3` and is written behind the for loop.

## open() Function and With Statement

In python, `open` function and with statemen is often used to work with resources like files or resources that need to be managed properly, such as network connections or database connections. 

**open() Function**

`open()` function is primarily used to open files and returns a file object that can be used to read from or write to the file, and it's essential to close the file after completing implementation, if the file is not closed properly, the further execution may lead to resouce leaks and cause issues.

The format of using open() function is:
```py
file_object = open("filename", "mode")
file_object.mode("If it's write or append mode we need to provide the content we want to add to the file")
file_object.close() # The close() is important!
```

"filename" is the name or path of the file, "mode" is the name of operation that we want to perform to the file, there are 5 modes usually used:
 - "r"(Read Mode): Open the file for reading, it raises an error if the file doesn't exist, the syntax is `.read()`.
 - "w"(Write Mode): Open the file for writing, if the file doesn't exist, it creates a new file, if the file exists, it will emtpy the file for the new data, the syntax is `.write()`.
 - "a"(Append Mode): Open the file for appending, if the file doesn't exist, it creates a new file, if the file exists, it will append the new data at the end of the existing data, notice that when we use "a" mode to append new data the syntax is also `.write()`.
 - "r+"(Read and Write Mode): Open the file for both reading and writing, it raises an error if the file doesn't exist, the write mode in this case will not empty the existing data.
 - "a+"(Append and Read Mode): Open the file for both appending and reading, if the file doesn't exist, it creates a new file, if the file exists, it will append the new data at the end of the existing data.

**With Statemen**

With statement provides a cleaner and more concise way to deal with the resouces, it makes sure the resouces are properly closed after the block of code inside the `with` statemen is executed, regardless of whether an exception occurs. With statement is commonly used with file operations and also network connections and database connections.

The format of with statement is:
```py
with open("filename", "mode") as file_object:
    file_object.mode("If it's write or append mode we need to provide the content we want to add to the file")
```

**Example**

Use open() function to create a file named "my_data.txt" and write some content in it:
```py
my_data = open("my_data.txt", "w")
my_data.write("This is my data.")
my_data.close()
```

Use with statement to make the same operations:
```py
with open("my_data.txt", "w") as my_data:
    my_data.write("This is my data.")
```

**Some read() bugs**

When we use "a+" and "r+" mode to add some new data to the file, and print the data immediately by reading it, the console will not print the data we expect, this is because when the adding data operations complete executing, the file pointer moves to the end of the file, it can not reach the file from the beginning, if we want to make sure it always read the file from the beginning, we can use the `.seek()` function to do that.

## Dunder/Magic Method
