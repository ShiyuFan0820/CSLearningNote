# Pass by Value and Pass by Reference

Pass by value and pass by reference refer to how arguments are passed to functions and how the original arguments can be affected.

Actually, Python doesn't have true pass by reference as understood in languages like C++, in Python, arguments are passed by object reference, but this can be similar to the behaviour in other languages, so let's look at the examples in Python below. 

## Pass by Value

Pass by value will not affect the original argument. When pass the value to a function, it passes a copy of the value to the function, this means that any changes made to the argument within the function do not affect the original variable outside the function:
```py
def pass_by_value(int_val):
    int_val **= 2
    print(f"Integer value after passing in: {int_val}")\

# Test
num_test = 4
print(f"Original integer value: {num_test}")
pass_by_value(num_test)
print(f"Original integer value after function call: {num_test}")
```

The output is:

<div align=center>
<img width="500" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/907e5c3c-cb5f-4d12-8554-3ea308a5645f">
</div>

## Pass by Reference

Pass by reference pass a reference to the original variable to the function, this means that changes made to the argument within the function affect the original variable outside the function:
```py
def pass_by_refer(list_val):
    list_val.append("Add")
    print(f"List value after passing in: {list_val}")


#Test
list_test = [1, 2, 4]
print(f"Original list : {list_test}")
pass_by_refer(list_test)
print(f"Original list after function call: {list_test}")
```

The output is:

<div align=center>
<img width="500" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/8b245f8d-9d19-43c6-bdb0-3fc06ab17f98">
</div>
