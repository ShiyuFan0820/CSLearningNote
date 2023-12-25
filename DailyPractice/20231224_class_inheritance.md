# Class Inheritance

**Exercise: Me and My Cute Pets**

1. Given an Animal class, inheritanting the Animal class by pets you want to keep.
2. Redefine the methods in the Animal class if the pets are not suitable for the original version.
3. Define a Human class to adopt the animals.

**The code is:**
```py
class Animal:
    def __init__(self, name, position, type):
        self.m_name = name
        self.m_position = position
        self.m_type = type
        print(f"{self.m_name} born at position {self.m_position}.")
        
    def walk(self, new_position):
        print(f"{self.m_name} moved from {self.m_position} to {new_position}.")
        self.m_position = new_position
        
    def swim(self, new_position):
        print(f"{self.m_name} swam from {self.m_position} to {new_position}.")
        self.m_position = new_position
    
    def poo_poo(self, new_position):
        print(f"{self.m_name} went to {new_position} to poop.")
        
class Pig(Animal):
    def swim(self, new_position):
        print(f"{self.m_name} is a pig 🐷, and cannot swim!")
        

class KomodoDragon(Animal):
    def walk(self, new_position):
        print(f"{self.m_name} is a komodo dragon 🦎, don't try to walk it, it will eat you alive!")


class Fish(Animal):
    def walk(self, new_position):
        print(f"{self.m_name} is a fish 🐟 and cannot walk!")
    

class Human():
    def __init__(self, name, position, animals):
        self.m_name = name
        self.m_position = position
        self.m_pets = animals
        for animal in animals:
            print(f"{self.m_name}, is adopting a {animal.m_type}, named {animal.m_name}.")
        
        
    def walk(self, new_position):
        print(self.m_name, "moved from", self.m_position, "to", new_position)
        self.m_position = new_position
        for animal in self.m_pets:
            animal.walk(new_position)
            
    def swim(self, new_position):
        for animal in animals:
            print(f"{self.m_name} took {animal.m_name} to swim.")
            animal.swim(new_position)
            
    def poo_poo(self, new_position):
        for animal in animals:
            print(f"{self.m_name} took {animal.m_name} to poop.")
            animal.poo_poo(new_position)
            

pig = Pig("Xixi", [2, 1], "🐷")
komodo_dragon = KomodoDragon("Koko", [2, 3], "🦎")
fish = Fish("Ariel", [7, 7], "🐟")
animals = [pig, komodo_dragon, fish]
human = Human("Fanfan", [1, 1], animals)
human.walk([6, 1])
human.swim([8, 1])
human.poo_poo([12, 12])
```

**Run the code:**
```py
Xixi born at position [2, 1].
Koko born at position [2, 3].
Ariel born at position [7, 7].
Fanfan, is adopting a 🐷, named Xixi.
Fanfan, is adopting a 🦎, named Koko.
Fanfan, is adopting a 🐟, named Ariel.
Fanfan moved from [1, 1] to [6, 1]
Xixi moved from [2, 1] to [6, 1].
Koko is a komodo dragon 🦎, don't try to walk it, it will eat you alive!
Ariel is a fish 🐟 and cannot walk!
Fanfan took Xixi to swim.
Xixi is a pig 🐷, and cannot swim!
Fanfan took Koko to swim.
Koko swam from [2, 3] to [8, 1].
Fanfan took Ariel to swim.
Ariel swam from [7, 7] to [8, 1].
Fanfan took Xixi to poop.
Xixi went to [12, 12] to poop.
Fanfan took Koko to poop.
Koko went to [12, 12] to poop.
Fanfan took Ariel to poop.
Ariel went to [12, 12] to poop.
```
