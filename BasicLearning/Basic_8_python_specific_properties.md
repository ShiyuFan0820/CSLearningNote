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

## Pickle

