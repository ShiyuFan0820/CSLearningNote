# Variables

A variable is an abstract concept that can store the result of a calculation or represent a value while the program is running.

In short, a variable is used to record data when a program is running.

## Int

Int is a kind of variable consists of integer, for example: 2, -2.

## Float

A float is a data type consists of a number that is not an integer, because it includes a fraction represented in decimal format. For example: 13.14, -13.14.

## Double

A double is double-precision floating-point number.

## String

String is a type of variable which can represent text, and it must be enclosed in double quotes at both ends. For example: "This is a string"

# Question: How to represent floating point numbers in binary？(Updateing～）

## Floating Point Decimal Number to Binary

**Floating point numbers in standard scientific notation**

For example:

```math
7.17 \times 10^7
```

```math
3.14 \times 10^5
```

```math
4.145 \times 10^{-9}
```

A floating point number has two parts - **mantissa** and **exponent**. The part of float number like "7.17", "3.14", or "4.145", is called mantissa. The part of the notation like the "7", "5", or "-9" next to "10" is called exponent. The number of digits of mantissa and exponent will be given in condition.

If the mantissa of the floating point number wants to float the point to the right or left, the number of the exponent will subtract or add the number, according to the movement the point made.

For example:

```math
7.17 \times 10^7 = 717 \times 10^{7-2} = 717 \times 10^5
```

```math
7.17 \times 10^7 = 0.0717 \times 10^{7+2} = 0.0717 \times 10^9
```

In binary, the principle is the same.

**Converting**

Follow the steps below:

- Split the number up in two parts, convert the two parts separately. The part on the left of the decimal point use succesive divisions by 2 and collect the reminders from bottom to top,
- The part on the right of the decimal point use succesive multiplications by 2, and strip off the result on the left of the decimal, continue until result on the right of the decimal point is either zero or repeatition, collect the whole number results from top to bottom,
- Collect the result of the two parts,
- Normalize the results requests us to move the floating point to the left of a actual number. In binary representation, we use the left most bit of mantissa and exponent to represent negative or positive, "0" represent positive, and "1" represent negative.

For example:

```math
23.375(10)=(???)(2)
```
1. Split up

Split up 23.375 to 23 and 0.375.
```math
23(10)=10111(2)
```
2. Succesive multiplications

```math
2 \times 0.375 = 0.75
```

Strip off the left of decimal point is 0.75:

```math
2 \times 0.75 = 1.5
```

Strip off the left of decimal point is 0.5:

```math
2 \times 0.5 = 1.0
```
The right of the decimal point is "0", multiplications end.

The result is:

```math
0.375(10)=0.011(2)
```
3. Collect results

The results number is:

```math
23.375(10)=10111.011(2)
```

4. Normalize

Float the point to the beginning of a actual number of the binary number:

```math
10111.011(2) = 0.10111011 \times 2^5
```

Both mantissa and exponent are positive, so their sign bits are both 0. The exponent is "5", it shoule be converted to binary, 5(10) = 101(2).

So the result is:

```math
23.375(10) = 0.10111011 \times 2^{101}(2)
```



## Floating point Binary Number to Decimal

For example:

![](https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/dea074ee-e6c5-479c-98a8-730273aae808)

1. Positive and negative judgment

In binary,both mantissa and exponent are stored in two's complement, the leftmost bit of mantissa or exponent is called the sign bit, if it is a positive number, the sign bit will be 0, if it is a negative number, the sign bit will be 1.  
The ture form, one's complement code, and two's complement code are same when the mantissa is positive, when the mantissa is negative, to get one's complement, replace "0"s with "1"s and vice versa except the sign bit, to get two's complement, add "1" to the result of the one's complement.

In this binary number, ten bits on the left have been allocated to the mantissa, and six bits on the right have been allocated to the exponent.  
In the mantissa part, the leftmost of it is the sign bit of the mantissa which is zero, means this number is a positive number, and we do not need to convert it to ture form. In the exponent part, the condition is the same, means the exponent is also positive.

2. Coverting exponent
![](https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/babd6996-a180-4f84-8115-2f096c662969)

In binary, 11（2） = 3（10）, so the exponent is 3. Like 10 is the base number in decimal, 2 is base number in binary, so the exponent part is 2 to the power of 3.  
So in this 16 bits number, there is something times 2 to the power of 3.

3. Coverting mantissa
![](https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/dd1aae74-6189-4479-bd9a-b377f2568ce8)

An imaginary point is right after the sign bit. As the exponent is 3, we can move the imaginary point back three places and we get the pure binary number.

![](https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/8d219b80-34d3-4f30-8ec4-bb9c5c459f7b)

Then we can convert it to decimal.
```math
110.1(2) = 6.5(10)
```

So the float number converts to decimal is:
```math
0110100000000011(2)=6.5(10)
```

















