# Function Overloading

Function overloading refers to the ability to define multiple functions with the same name but different numbers of parameters or different types of parameters, this allows user to use the same function name for different implementations based on the type or number of the parameters passed to it.

For example:

Function `add` in here is an overlodaing function.
```c
#include<iostream>

int add(int a, int b){
    std::cout<<"Function add 1 is called, the result is ";
    return (a + b);
}

int add(int a, int b, int c){
    std::cout<<"Function add 2 is called, the result is ";
    return (a + b + c);
}

double add(double a, double b){
    std::cout<<"Function add 3 is called, the result is ";
    return (a + b);
}

double add(double a, double b, double c){
    std::cout<<"Function add 4 is called, the result is ";
    return (a + b + c);
}

int main()
{
    std::cout<<"Call add 1: "<<add(1, 2)<<std::endl;
    std::cout<<"Call add 2: "<<add(1, 2, 1)<<std::endl;
    std::cout<<"Call add 3: "<<add(1.5, 2.1)<<std::endl;
    std::cout<<"Call add 4: "<<add(1.5, 2.1, 1.2)<<std::endl;
    return 0;
}
```

The output is:
```c
Call add 1: Function add 1 is called, the result is 3
Call add 2: Function add 2 is called, the result is 4
Call add 3: Function add 3 is called, the result is 3.6
Call add 4: Function add 4 is called, the result is 4.8
```
