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

## Polymorphism

**Polymorphism** means "many forms". It allows objects of different classes to be treated as objects of a common base class. In Python, polymorphism is achieved when different classes have methods with the same name but different implementations.

```python
class Dog:
    def make_sound(self):
        return "Woof!"

class Cat:
    def make_sound(self):
        return "Meow!"

class Duck:
    def make_sound(self):
        return "Quack!"

# Create different animals
animals = [Dog(), Cat(), Duck()]

# Same method name, different sounds
for animal in animals:
    print(animal.make_sound())
```

**Output:**
```
Woof!
Meow!
Quack!
```

Here, each animal class has a `make_sound()` method, but each implements it differently. The same method name produces different behaviors based on the object type. This demonstrates the power of treating different objects uniformly, similar to how we can store objects of different classes in lists as shown in Chapter 3.

## Abstraction

**Abstraction** hides complex implementation details and shows only the essential features. In Python, abstraction is achieved through abstract classes and methods using the `abc` module. However, for beginners, it's enough to understand that abstraction means **hiding complexity** and providing simple interfaces.

```python
# Simple abstraction example - user doesn't need to know how microwave works inside
class Microwave:
    def __init__(self):
        self.power = 0
        self.time = 0
    
    def heat_food(self, food, minutes):
        self._set_power(800)     # Hidden complexity
        self._set_timer(minutes) # Hidden complexity
        self._start_heating()    # Hidden complexity
        print(f"Your {food} is ready!")
    
    def _set_power(self, watts):  # Private method (hidden)
        self.power = watts
        print(f"Power set to {watts} watts")
    
    def _set_timer(self, minutes):  # Private method (hidden)
        self.time = minutes
        print(f"Timer set to {minutes} minutes")
    
    def _start_heating(self):  # Private method (hidden)
        print("Heating started...")

# User only needs to know this simple interface
microwave = Microwave()
microwave.heat_food("pizza", 2)
```

**Output:**
```
Power set to 800 watts
Timer set to 2 minutes
Heating started...
Your pizza is ready!
```

## Encapsulation

**Encapsulation** bundles data and methods into a single unit (class) and restricts access to some components. In Python, encapsulation is achieved using **private attributes** and **methods** by prefixing them with underscore(s). Note that while private attributes and methods are intended to be hidden from the user, it is not a strict rule and can be bypassed in Python. This concept will become important when we create graphics programs with Turtle (Chapter 6) and games with Pygame (Chapter 7), where we often want to hide complex implementation details from the user.

```python
class PiggyBank:
    def __init__(self):
        self._coins = 0         # Protected attribute
        self.__secret_code = 1234  # Private attribute
    
    def add_coin(self):
        self._coins += 1
        print(f"Added a coin! Total coins: {self._coins}")
    
    def get_coins(self):
        return self._coins
    
    def open_bank(self, code):
        if code == self.__secret_code:
            print(f"Bank opened! You have {self._coins} coins!")
            return self._coins
        else:
            print("Wrong code! Bank stays locked!")
            return 0
    
    def __count_money(self):  # Private method
        return self._coins * 25  # Each coin worth 25 cents

bank = PiggyBank()
bank.add_coin()
bank.add_coin()
bank.add_coin()
print(f"Current coins: {bank.get_coins()}")
bank.open_bank(1234)  # Correct code
bank.open_bank(9999)  # Wrong code
```

**Output:**
```
Added a coin! Total coins: 1
Added a coin! Total coins: 2
Added a coin! Total coins: 3
Current coins: 3
Bank opened! You have 3 coins!
Wrong code! Bank stays locked!
```

---

## Navigation

⬅️ **[Previous: Chapter 3 - Objects](chapter-03.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 5 - Import and Modules](chapter-05.md)**