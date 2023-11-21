# What Are Iteration And Recursion

## Iteration

If there are numbers in a given range, the programme will loop throught the numbers one by one automatically until the order to end is given. This process is called iteration.

## Recursion

Recuesion is a function that calls itself from within.

# Fibonacci Sequence In Iteration And Recursion

## Fibonacci Sequence

Fibonacci sequence is a kind of number sequence where the next value always equals the sum of it's two previous values.

## Fibonacci In Iteration

```py
def fibonacci(index):
    if index <= 1:
        print(index)
    else:
        num1 = 0
        num2 = 1
        for i in range(index):
            result = num1 + num2
            num1 = num2
            num2 = result
        return num1
```

# Iteration vs Recursion
