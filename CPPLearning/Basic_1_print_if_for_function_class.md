# Print

1. `<iostream>` is a library that provides functionality for input and output. This means including the input/output stream library.
2. `int main`, main function, the entry point of the program.
3. `std::cout` is an object of the `std::ostream` class, which is used to output data to the console.
4. `<<` operator is the insertion operator, and it's used to insert data into the `std::cout` object, in this case, `Hello Fanfan` is being inserted. `<< std::endl` is used to insert a newline like `\n`, it moves the cursor to the next line after printing `Hello Fanfan!`.
5. In C++, the "main" function must return an integer value indicating the exit status of the program. Typically, returning 0 indicates successful program execution, while returning a non-zero value indicates an error.

```c
#include <iostream>

int main() { 
    std::cout << "Hello Fanfan!" << std::endl;
    return 0; 
}
```

# If 

```c
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

```c
#include <iostream>

int main() {
    for (int i = 0; i < 5; i++) {
        std::cout << "The value of i is " << i << std::endl;
    }
    return 0;
}
```

# Class
