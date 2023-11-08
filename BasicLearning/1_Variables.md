# Variables

A variable is an abstract concept that can store the result of a calculation or represent a value while the program is running.

In short,a variable is used to record data when a program is running.

## Int

Int is a kind of variable consists of integer,for example:2,-2.

## Float

A float is a data type consists of a number that is not an integer, because it includes a fraction represented in decimal format.For example:13.14,-13.14

## Double

A double is double-precision floating-point number.

## String

String is a type of variable which can represent text,and it must be enclosed in double quotes at both ends.For example:"This is a string"

# Question：How to represent floating point numbers in binary？(Updateing～）

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

A floating point number has two parts- mantissa and exponent.The part of float number like "7.17","3.14",or "4.145",is called mantissa.The part of the notation like the "7","5",or "-9" next to "10" is called exponent.The number of digits of mantissa and exponent can be customized.

In binary,both mantissa and exponent are stored in two's complement,an imaginary binary point is located immediately to the right of the sign bit(the leftmost bit).

If the mantissa is a positive number,the sign bit will be 0,if the mantissa is a negative number,the sign bit will be 1.Same with the exponent.

