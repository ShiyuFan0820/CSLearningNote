# Input

In C++, user input can be taken by using the `cin`, short for `character input`, which is a part of the `iostream` library.

**How to take input**

1. First, include the `iostream` header, which is necessary for input and output operations.
2. Write the main function which is the entry point of the C++ program, this is where the code will be written to take user input.
3. Use `cin` to take input from the user, `>>` operator is used to extract the data from the input stream.

**Example**

This is a simple example of asking the user's name and age.
```c
#include <iostream>

int main() {
    std:: string name; // Variable to store the user's name
    int age; // Variable to store the user's age
    
    std::cout<<"What's your name: "; // Prompt the user for their name
    std::cin>>name; // Read the input into the name variable
    
    std::cout<<"What's your age: "; //Prompt the user for their age
    std::cin>>age; // Read the input into the age variable
    
    // Display the information back to the user
    std::cout<<"Hello, "<<name<<"! Your are "<<age<<" years old!"<<std::endl;
    return 0;
}
```




