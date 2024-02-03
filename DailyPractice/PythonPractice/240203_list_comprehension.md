# List Comprehension

**Exercise:**

1. Given a list of strings `list_of_string = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55]`.
2. Use list comprehension to convert the list_of_strings to a list of integers.
3. Then use list comprehension again to create a new list called result. This new list should only contain the even numbers from the list numbers.

**The code is:**
```py
list_of_string = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55]
list_of_int = [int(string) for string in list_of_string]
result = [int for int in list_of_int if int % 2 == 0]
print(result)
```

**The ouput is:**
```py
[2, 8, 34]
```
