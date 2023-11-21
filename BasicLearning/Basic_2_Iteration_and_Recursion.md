# What Are Iteration And Recursion

## Iteration

If there are numbers in a given range, the programme will loop throught the numbers one by one automatically until the order to end is given. This process is called iteration.

## Recursion

Recuesion is a function that calls itself from within.

# Fibonacci Sequence In Iteration And Recursion

## Fibonacci Sequence

Fibonacci sequence is a kind of number sequence where the next value always equals the sum of it's two previous values. For example:
|No.0|No.1|No.2   |No.3 |No.4  |No.5  |No.6  |No.7  |No.8|
|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|0    |1  |1(0+1)|2(1+1)|3(1+2)|5(2+3)|8(3+5)|13(5+8)|21(8+13)|
## Fibonacci In Iteration

```py
def fibonacci(index):
        num0 = 0
        num1 = 1
        for i in range(index):
            result = num0 + num1
            print(num0)
            num0 = num1
            num1 = result
```

## Fibonacci In Recursion

# Iteration vs Recursion
