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

_Follow the steps below:_

- Covert the integer part: Split the number up in two parts, convert the two parts separately. The part on the left of the decimal point use succesive divisions by 2 and collect the reminders from bottom to top,
- Convert the decimal part: The part on the right of the decimal point use succesive multiplications by 2, and strip off the result on the left of the decimal, continue until result on the right of the decimal point is either zero or repeatition, collect the whole number results from top to bottom,
- Combine the integer and decimal part,
- Add sign bit: In binary representation, we use the left most bit of mantissa and exponent as a sign bit to represent negative or positive, "0" represent positive, and "1" represent negative.
- If you want to use a negative decimal number to convert to a binary number then to do the arithmetic, you need to convert the true form to the two's complement because in binary, both mantissa and exponent are stored in two's complement, to get the two's complement, replacing "0"s with "1"s and vice versa except the sign bit to get the one's complement first, then add "1" to get the result of the one's complement, to get the two's complement.

**Example 1(Positive number):**

```math
23.375(10)=(???)(2)
```
1. Convert the integer part

Split up 23.375 to 23 and 0.375.
```math
23(10)=10111(2)
```
2. Convert the decimal part

```math
2 \times 0.375 = 0.75
```
So the first bit is "0".

Strip off the left of decimal point is 0.75:

```math
2 \times 0.75 = 1.5
```
So the second bit is "1".

Strip off the left of decimal point is 0.5:

```math
2 \times 0.5 = 1.0
```
So the third bit is "1", and the right of the decimal point is "0", multiplications end.

The result is:

```math
0.375(10)=0.011(2)
```
3. Combine the two parts

The results number is:

```math
23.375(10)=10111.011(2)
```

4. Add sign bit

Both mantissa and exponent are positive, so their sign bits are both 0.

So the result is:

```math
23.375(10) = 10111.011(2)
```

**Example 2(Negative number):**

```math
-3.125(10) = ???(2)
```

1. Convert the integer part

As the number is negative, we can calculate the positive form of it fisrt, the integer part of "3.125" is "3", so the binary representation is:
```math
3(10) = 11(2)
```
   
2. Convert the decimal part

```math
2 \times 0.125 = 0.25
```

So the first bit is "0".

```math
2 \times 0.25 = 0.5
```

So the second bit is "0".

```math
2 \times 0.5 = 1.0
```

So the third bit "1", and the right of the decimal point is "0", mutiplications end.

So the result is:
```math
0.125(10) = .001(2)
```

3. Collect results

Combine the integer and decimal part to get the final binary representation is:
```math
3.125(10) = 11.001(2)
```
   
4. Add sign bit

Since the original number is negative, add a sign bit "1" for negative, so the result is:
```math
-3.125(10) = 111.001(2)
```

## Floating point Binary Number to Decimal

_Follow the step blow:_ 

- Identify the sign bit(leftmost bit),
- Convert integer part: Convert the integer part of the binary number(excluding the sign bit) to decimal using the binary-to-decimal convertion method.
- Convert fractional part: Convert the fractional part of the binary number to decimal by multiplying each bit by 2<sup>-n</sup>, where "n" is the position of the bit.
- Combine integer and fractional parts: Add the decimal values obtained from the integer and fractional parts, if the sign bit is "1", the final result is negative.

**Example:**

_Convert the negative binary number 1100.101 to decimal._

1. Identify the sign bit

The sign bit is "1", indicating the number is negative.

2. Convert the integer part
```math
100(2) = 4(10)
```

3. Convert the fractional part
```math
0.101(2) = 1 \times 2^{-1} + 0 \times 2^{-2} + 1 \times 2^{-3} = 0.625(10)
```

4. Combine integer and fractional parts

The result is:
```math
1100.101(2) = -4.625(10)
```

## 16 Bits Folating Point Binary Number to Decimal

_Follow the step below:_

- Positive and negative judgment: The leftmost bit of mantissa or exponent is called the sign bit, if it is a positive number, the sign bit will be 0, if it is a negative number, the sign bit will be 1(We already mentioned above).  
- Convert exponent: Using the binary to decimal method to convert the exponent, the number converted is the 2 to the power of the convert number(be careful with the positive and negative),
- Convert mantissa: An imaginary point is right after the sign bit, If the mantissa is positive, move the imaginary point according to the exponent to get the pure binary number(When the exponent is positive, move the imaginary point to the right and vice versa).   Convert the pure binary number to decimal, when the sign bit is positive, using the binary-to-decimal method. When the sign bit is negative, the integer part of the binary number to decimal by multiplying each bit by 2<sup>n-1</sup>, the fractional part of the binary number to decimal by multiplying each bit by 2<sup>-n</sup>, where "n" is the position of the bit, but the sign bit should multiple the negative place value.

**Example 1(Positive number):**

![](https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/dea074ee-e6c5-479c-98a8-730273aae808)

1. Positive and negative judgment

In this binary number, ten bits on the left have been allocated to the mantissa, and six bits on the right have been allocated to the exponent.  
In the mantissa part, the leftmost of it is the sign bit of the mantissa which is "0", indicating this number is a positive number, and we do not need to convert it to ture form. In the exponent part, the condition is the same, indicating the exponent is also positive.

2. Covert exponent
![](https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/babd6996-a180-4f84-8115-2f096c662969)

In binary, 11（2） = 3（10）, so the exponent is 3. Like 10 is the base number in decimal, 2 is base number in binary, so the exponent part is 2 to the power of 3.  
So in this 16 bits number, there is something times 2 to the power of 3.
 
3. Covert mantissa
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

**Example 2(Negative number):**

![](https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/868a02ca-0d4d-4a09-a8bc-941317b846a4)

1. Positive and negative judgment

In this binary number, ten bits on the left have been allocated to the mantissa, and six bits on the right have been allocated to the exponent.  
In the mantissa part, the sign bit of the mantissa is "1", indicating this number is a negative number.

2. Convert exponent

In binary, 11（2） = 3（10）, so the exponent is 3. So in this 16 bits number, there is something times 2 to the power of 3.

3. Convert mantissa

![](https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/c27eccb2-5df0-4235-8e23-58bcb4d4f0ff)

An imaginary point is right after the sign bit. As the exponent is 3, we can move the imaginary point back three places and we get the pure binary number, which is "1110.1".

Convert to decimal is:
```math
1110.1(2) = 1 \times -2^8 + 1 \times 2^2 + 1\times 2^1 + 0 \times 2^0 + 1 \times 2^{-1} = -1.5
```

So the result is:

```math
1110100000000011(2) = -1.5(10)
```












