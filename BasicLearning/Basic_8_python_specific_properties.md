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

The generator in Python looks like a function which returns a generator object, e.g. object can be iterated on, the difference is that generator object can generate values as needed(also called lazily evaluation), rather than generating and storing all values at once like what for loop and while loop do, it essentially turns an iterable (An iterable is any object that can be iterated over, meaning it can be used in a loop, like lists, strings, tuples and dictionaries) into an iterator (An iterator is an object that represents a stream of data. It implements the iterator protocol, which requires methods like `__iter__()` and `__next__()`).

Generator can be defined by using generator function or generator expression. 

**Generator Function**

Defining a generator function is like defining a normal function, but it uses `yield` to get one value at one time rather than `return`, when we call a generator function, it returns a generator object without actually excuting the body of the function, we can call the generator function succssively, it resumes excution from where it last yielded a value, this allows to continue generating values from where if previously left off.

_Example of How a Generator Function Works:_


**Generator Expression**


_Example of How a Generator Expression Works:_


**What's the Benefit of Using Generators?**

## Decorator


## List Comprehension
