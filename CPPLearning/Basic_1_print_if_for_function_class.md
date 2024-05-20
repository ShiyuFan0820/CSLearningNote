# Print

1. `<iostream>` is a library that provides functionality for input and output. This means including the input/output stream library.
2. `int main`, main function, the entry point of the program.
3. `std::cout` is an object of the `std::ostream` class, which is used to output data to the console.
4. `<<` operator is the insertion operator, and it's used to insert data into the `std::cout` object, in this case, `Hello Fanfan` is being inserted. `<< std::endl` is used to insert a newline like `\n`, it moves the cursor to the next line after printing `Hello Fanfan!`.
5. In C++, the "main" function must return an integer value indicating the exit status of the program. Typically, returning 0 indicates successful program execution, while returning a non-zero value indicates an error.

```c++
#include <iostream>

int main() { 
    std::cout << "Hello Fanfan!" << std::endl;
    return 0; 
}
```

# If 

```c++
#include <iostream>

int main() {
    int x = 10;
    if (x > 5) {
        std::cout << "x is greater than 5." << std::endl;
    } else {
        std::cout << "x is not greater than 5." << std::endl;
    }
    return 0;
}
```

# For

In C++, the for loop syntax is a bit different from that in Python.
1. `int i = 0`, this initialises the loop variable `i` to 0.
2. `i < 5`, this is the condition that the loop checks before each iteration, if it's true, the loop continues, if it's false, the loop terminates.
3. `i++`, this is the update expression that increments `i` by `1` after each iteration.

```c++
#include <iostream>

int main() {
    for (int i = 0; i < 5; i++) {
        std::cout << "The value of i is " << i << std::endl;
    }
    return 0;
}
```

# Class

1. `class Person { ... };`, this declares a class named `Person`. Inside the class definition:
- `private`: It indicates that the member variables below it are only accessible within the class, `std::string m_name;` and `int m_age;`: These are member variables of the `Person` class. They represent the name and age of the person.
- `public`: It indicates that the member functions and variables below it are accessible from outside the class.
- `Person(std::string name, int age) { ... }`: This is the constructor of the `Person` class. It initializes the `m_name` and `m_age` member variables with the values passed as arguments.
- `void displayInfo() { ... }`: This is a member function of the Person class. It outputs the name and age of the person. In C++, the `void` keyword is used to specify that a function does not return any value.
- `~Person() { ... }`: This is a destructor for the `Person` class. It is called automatically when an object of the class goes out of scope or is explicitly deleted. In this example, the destructor simply prints a message indicating that it has been called.

```c++
#include <iostream>

// Define a simple class named Person.
class Person {
    private: // Member variables
    std::string m_name;
    int m_age;
    public: // Constructor
    Person(std::string name, int age) {
        m_name = name;
        m_age = age;
    }
    // Member function to display information about the person.
    void displayInfo() {
        std::cout << "Name: " << m_name << ", Age: " << m_age << std::endl;
    }
    ~Person() {
        std::cout << "Destructor called for " << m_name << "." << std::endl;
    }
};

int main() {
    // Create an object of class Person.
    Person person1("Fanfan", 20);
    // Call the displayInfo() member function.
    person1.displayInfo();
    return 0;
}
```
