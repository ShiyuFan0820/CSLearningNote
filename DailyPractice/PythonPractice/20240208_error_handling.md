# Error Handling

**Exercise 1: Index Error Handling**

1. Given a buggy code, there will be an index error if you run the code directly.
2. Modify the code, prevent it from crashing.
3. If the index is out of range, the final output should be "Fruit pie".

The Given code:
```py
fruits = ["Apple", "Orange", "Peach"]


def make_pie(Index):
  fruit = fruits[Index]
  pirnt(fruit + " pie")


make_pie(4)
```

Modified code:
```py
fruits = ["Apple", "Orange", "Peach"]


def make_pie(Index):
  try:
    fruit = fruits[Index]
  except IndexError:
    print("Fruit pie")
  else:
    pirnt(fruit + " pie")


make_pie(4)
```
