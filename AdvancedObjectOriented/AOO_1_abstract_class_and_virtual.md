# Abstract Class and Virtual

## What is Abstract Class?

An abstract class is a class that can't be instantiated on its own (This means an instance can not be created directly from the abstract class itself). This is becuase an abstract class often contains at least one or more abstract methods.

An abstract method in an abstract class is a method that is declared but does not contain an implementation (i.e., it has no code inside this method). This means that the abstract method or the abstract class self is incomplete, so it can not create an instance directly.

To create an instance of an abstract class, a subclass should be created, and complete implementations for all abstract methods defined in the abstract class.

## How Abstract Class Works?

In Python, import `ABC` and `abstractmethod` first, then abstract class can be created, take the `Animal` class which was written previously as example:

```py
# Import ABC and abstractmethod.
from abc import ABC, abstractmethod

# Make the Animal class an abstract class.
class Animal(ABC): # Don't forget to inherit from ABC.
    def __init__(self, name, position):
        self.m_name = name
        self.m_position = position
        print(f"{self.m_name} born at position {self.m_position}.")

    # When want to create an abstract method use @abstractmethod decorator.
    @abstractmethod
    def move(self, new_position):
        pass


# Every abstract method declared in the supclass must contains implementation in the subclass.
class Pig(Animal):
    def walk(self, new_position):
        print(f"{self.m_name} is lazy, and doesn't want to be walked.")


class KomodoDragon(Animal):
    def walk(self, new_position):
        print(f"{self.m_name} is a komodo dragon 🦎, don't try to walk it, it will eat you alive!")


class Fish(Animal):
    def walk(self, new_position):
        print(f"{self.m_name} is a fish 🐟 and cannot walk!")


# Test example
pig = Pig("Xixi", (1, 1))
```

When run the test code, an error will be raised, because abstract methods haven't add implementations in the subclass:

<div align=center>
<img width="550" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/a21c49b5-e50f-4207-b94f-7113dd9f21d9">
</div>

Add implementations for every abstract method in every subclass:
```py
# Import ABC and abstractmethod.
from abc import ABC, abstractmethod

# Make the Animal class an abstract class.
class Animal(ABC): # Don't forget to inherit from ABC.
    def __init__(self, name, position):
        self.m_name = name
        self.m_position = position
        print(f"{self.m_name} born at position {self.m_position}.")

    # When want to create an abstract method use @abstractmethod decorator.
    @abstractmethod
    def move(self, new_position):
        pass


# Every abstract method declared in the supclass must contains implementation in the subclass.
class Pig(Animal):
    # The argument should be the same as the argument of the abstract method of the supclass.
    def move(self, new_position):
        print(f"{self.m_name} is a pig, he walked to new position {new_position}.")

    def walk(self, new_position):
        print(f"{self.m_name} is lazy, and doesn't want to be walked.")

class KomodoDragon(Animal):
    def move(self, new_position):
        print(f"{self.m_name} is a komodo dragon, she climbed to new position {new_position}.")

    def walk(self, new_position):
        print(f"{self.m_name} is a komodo dragon 🦎, don't try to walk it, it will eat you alive!")


class Fish(Animal):
    def move(self, new_position):
        print(f"{self.m_name} is a fish, he swam to new position {new_position}.")

    def walk(self, new_position):
        print(f"{self.m_name} is a fish 🐟 and cannot walk!")


# Test example
pig = Pig("Xixi", (1, 1))
komodo = KomodoDragon("Coco", (0, 0))
fish = Fish("Mac", (7, 7))
pig.move((7, 1))
komodo.move((2, 3))
fish.move((4, 5))

```

The output is:
```py
Xixi born at position (1, 1).
Coco born at position (0, 0).
Mac born at position (7, 7).
Xixi is a pig, he walked to new position (7, 1).
Coco is a komodo dragon, she climbed to new position (2, 3).
Mac is a fish, he swam to new position (4, 5).
```

## Why Abstract Class is Needed?
