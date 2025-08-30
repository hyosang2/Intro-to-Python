---
layout: default
title: Chapter 4 - OOP Principles
---

# Chapter 4: Principles of OOP

There are four principles revolving OOP. The majority of these principles further allows us avoid repeating writing similar codes. These principles build upon the class and object concepts introduced in Chapters 2 and 3. In Python, only inheritance and polymorphism are used frequently throughout the development; however, it is good idea to have understandings in abstraction and encapsulation as well.

## Inheritance

**Inheritance** allows a class to inherit properties and methods from another class. The class that inherits is called the **child class** or **derived class**, and the class being inherited from is called the **parent class** or **base class**.

In Python, inheritance is defined by putting the parent class name in parentheses after the child class name. The `super()` function is used to call methods from the parent class, particularly useful for calling the parent's `__init__()` method.

```python
# Base class
class Vehicle:
    def __init__(self, name, speed):
        self.name = name
        self.speed = speed
        print(f"Created a {self.name} that goes {self.speed} mph!")
    
    def move(self):
        print(f"The {self.name} is moving at {self.speed} mph!")

# Child classes
class Car(Vehicle):
    def __init__(self, name, speed, doors):
        super().__init__(name, speed)
        self.doors = doors
        print(f"This car has {self.doors} doors.")
    
    def honk(self):
        print(f"The {self.name} goes BEEP BEEP!")

class Bicycle(Vehicle):
    def __init__(self, name, speed, has_bell):
        super().__init__(name, speed)
        self.has_bell = has_bell
    
    def ring_bell(self):
        if self.has_bell:
            print(f"The {self.name} goes RING RING!")
        else:
            print(f"The {self.name} doesn't have a bell.")

# Create vehicle objects
my_car = Car("Red Car", 60, 4)
my_bike = Bicycle("Blue Bike", 15, True)

# Use inherited and new methods
my_car.move()  # From Vehicle class
my_car.honk()  # Car's own method

my_bike.move()  # From Vehicle class
my_bike.ring_bell()  # Bicycle's own method
```

**Output:**
```
Created a Red Car that goes 60 mph!
This car has 4 doors.
Created a Blue Bike that goes 15 mph!
The Red Car is moving at 60 mph!
The Red Car goes BEEP BEEP!
The Blue Bike is moving at 15 mph!
The Blue Bike goes RING RING!
```

## Other OOP Principles

### Polymorphism
Polymorphism allows objects of different classes to be treated as objects of a common base class, while still calling their specific methods.

### Encapsulation
Encapsulation is the bundling of data and methods that work on that data within one unit (class), and restricting access to some of the object's components.

### Abstraction
Abstraction involves hiding complex implementation details while showing only the essential features of an object.

These principles work together to make code more organized, reusable, and maintainable in object-oriented programming.

---

## Navigation

⬅️ **[Previous: Chapter 3 - Objects](chapter-03.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 5 - Import and Modules](chapter-05.md)**