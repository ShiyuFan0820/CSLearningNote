# Decimal

Decimal is a common system used in our everyday life,there are ten numbers in this system,including 0,1,2,3,4,5,6,7,8,9，this system is used for everyday counting.

# Binary 

Binary only includes two numbers--0,1,because of the simplicity of this system,it is used by almost all computers and computer-based devices."0" means the computer or a system is off,"1" means the computer or a system is on.

# Other Number Systems

Meanwhile there are also some other systems,like octal and hexadecimal ect,the difinitions of them are similiar to decimal and binary.Octal includes eight numbers--from 0 to 7,however,the hexadecimal is a little bit different,it consists of ten numbers and six letters,which are 0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F,G.

# Decimal to Binary 

Decimal counting uses 0 through 9,begins with the rightmost position,when the availiable numbers for this position are exhausted,the number is reset to 0,and the next position (one position to the left) will turn to 1.For example,9+1=10,the maximum number of the first position is 1,if we add 1 to 9,the first position will turn to 0,the number on the left will change from 0 to 1,that's how the result of 10 came out.

Binary counting is exactly the same,the only difference is there are only 0 and 1 are availiable.For example,1+1=10, the maximum number of the first position is 1,if we add 1 to 1,the first position will turn to 0,the number on the left will change from 0 to 1,so 10 is the second number in binary system equal to 2 in decimal system.

# Rules

We already know how to count and add in these two systems,but what's the rules between them?
```math
1+0=1(2)->1(10)
```
```math
1+1=10(2)->2(10)
```
```math
1+1+1=10+1=11(2)->3(10)
```
```math
1+1+1+1=11+1=100(2)->4(10)
```
```math
1+1+1+1+1=100+1=101(2)->5(10)
```
```math
1+1+1+1+1+1=101+1=110(2)->6(10)
```
```math
1+1+1+1+1+1+1=110+1=111(2)->7(10)
```
```math
......
```

Decimal has one's position,ten's position,hundred's position,and thousand's position,etc.These positions represent $10^0$, $10^1$, $10^2$, $10^3$,etc.Same with the binary,it has one's position,two's position,four's position,and eight's position,etc.These positions represent $2^0$, $2^1$, $2^2$, $2^3$,etc.Every position in binary is a bit.
So the rules of converting binary to decimal is like:
```math
1(2)=1\times 2^0=1(10)
```
```math
10(2)=0\times 2^0+1\times 2^1=2(10)
```
```math
11(2)=1\times 2^0+1\times 2^1=3(10)
```
```math
100(2)=0\times 2^0+0\times 2^1+1\times 2^2=4(10)
```
```math
101(2)=1\times 2^0+0\times 2^1+1\times 2^2=5(10)
```
```math
......
```

# Maximum Int In 32 Bit

In binary the maximum number of every position is 1,so the maximum int in 32 bit is the number that there is 1 in 32 positions，converting to decimal is:
```math
1\times 2^{31} + 1\times 2^{30}+1\times 2^{29}+...+1\times 2^2+1\times 2^1+1\times 2^0=2^{32}-1.
```


