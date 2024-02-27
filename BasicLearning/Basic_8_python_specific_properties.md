# Python Specific Properties

## Python List vs Tuple

**Python List**

List in python is like array in other programming language like C, C++ and Java, but more flexible. It's an ordered collection of objects enclosed be square brackets and separated by commas, objects in a list can be arbitrary mixture of elements like numbers, strings or a nested list and so on. All elements in a list can be access by indexing, a list can be shrunk or grow, it's mutable.

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

Tuple's operations are similar to list, but tuple is immutable, appending or removing elements in a tuple is not allowed, and elements in a tuple are enclosed in parentheses instead of square brackets.

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

1. List is mutable and more versatile and suitable for scenarios where you need dynamic, mutable sequences of elements that can be modified or extended over time.
2. Tuple is immutable, since tuple is immutable, Python can optimize memory usage and execution speed.
3. Tuple is generally faster than list, especially for operations like iteration and indexing.
4. Tuple can be used to return multiple values from a function.
5. Tuple can be used as dictionary keys as its immutable property.

## Shallow and Deep Copy
