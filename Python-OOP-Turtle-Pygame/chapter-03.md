---
layout: default
title: Chapter 3 - OOP Principles
---

# Chapter 3: OOP Principles

There are four core principles of OOP. These principles help you write code that's organized, reusable, and easier to manage as your programs grow. They build on the class and object concepts from Chapter 2.

## Inheritance

**Inheritance** lets a class borrow properties and methods from another class, so you don't have to write the same code twice. The class that inherits is called the **child class**, and the class being inherited from is called the **parent class**.

In Python, you put the parent class name in parentheses after the child class name. The **`super()`** function calls methods from the parent class — most commonly, the parent's `__init__()`:

```python
class Animal:
    def __init__(self, name, sound):
        self.name = name
        self.sound = sound

    def speak(self):
        print(f"{self.name} says {self.sound}!")

    def __str__(self):
        return self.name

class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name, "Woof")  # Call parent's __init__
        self.breed = breed

    def fetch(self):
        print(f"{self.name} the {self.breed} fetches the ball!")

class Cat(Animal):
    def __init__(self, name, is_indoor):
        super().__init__(name, "Meow")
        self.is_indoor = is_indoor

    def purr(self):
        print(f"{self.name} is purring...")

buddy = Dog("Buddy", "Golden Retriever")
whiskers = Cat("Whiskers", True)

buddy.speak()      # Inherited from Animal
buddy.fetch()      # Dog's own method

whiskers.speak()   # Inherited from Animal
whiskers.purr()    # Cat's own method
```

**Output:**
```
Buddy says Woof!
Buddy the Golden Retriever fetches the ball!
Whiskers says Meow!
Whiskers is purring...
```

Both `Dog` and `Cat` inherit the `speak()` method from `Animal`, so we only had to write it once. Each child class then adds its own unique methods (`fetch`, `purr`).

### Method Overriding

A child class can **override** (replace) a method it inherited from the parent by defining a method with the same name. This lets child classes customize inherited behavior:

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name} makes a sound.")

class Dog(Animal):
    def speak(self):  # Overrides Animal's speak()
        print(f"{self.name} says Woof!")

class Cat(Animal):
    def speak(self):  # Overrides Animal's speak()
        print(f"{self.name} says Meow!")

generic = Animal("Some Animal")
buddy = Dog("Buddy")
whiskers = Cat("Whiskers")

generic.speak()
buddy.speak()
whiskers.speak()
```

**Output:**
```
Some Animal makes a sound.
Buddy says Woof!
Whiskers says Meow!
```

Even though `Dog` and `Cat` both inherit from `Animal`, each provides its own version of `speak()`. This is method overriding — and it leads directly into our next principle.

## Polymorphism

**Polymorphism** means "many forms." It's the idea that objects of different classes can be treated the same way if they share a common interface (like a method name). Combined with inheritance, this is very powerful:

```python
# Using the Animal, Dog, Cat classes from above

animals = [Dog("Buddy"), Cat("Whiskers"), Dog("Rex"), Cat("Luna")]

for animal in animals:
    animal.speak()  # Same method call, different behavior!
```

**Output:**
```
Buddy says Woof!
Whiskers says Meow!
Rex says Woof!
Luna says Meow!
```

The loop calls `speak()` on every animal without knowing or caring whether it's a Dog or a Cat. Each object responds in its own way. This is polymorphism — the same method name produces different behavior depending on the object's class.

This pattern is especially useful in games: you might have a list of `Enemy` objects where some are `Zombie`, some are `Ghost`, and some are `Dragon`, but your game loop just calls `enemy.update()` on each one and lets polymorphism handle the rest.

## Encapsulation

**Encapsulation** bundles data and methods into a single unit (a class) and controls access to some parts. The idea is to hide internal details so that outside code only interacts with the object through its public methods — like how you use a microwave by pressing buttons without needing to know how the circuits inside work.

In Python, encapsulation is achieved by convention using **underscores** in names:

- A single underscore `_var` signals: *"this is meant to be internal — please don't touch it directly."* Python won't stop you, but other programmers will know it's not part of the public interface.
- A double underscore `__var` triggers **name mangling**: Python renames the variable to `_ClassName__var`, making it harder to access accidentally from outside. This helps avoid name clashes in child classes.

Neither is truly "private" the way some other languages enforce it — in Python, these are **conventions** rather than strict rules.

```python
class PiggyBank:
    def __init__(self):
        self._coins = 0              # Internal (by convention)
        self.__secret_code = 1234    # Name-mangled (harder to access)

    def add_coin(self):
        self._coins += 1
        print(f"Added a coin! Total: {self._coins}")

    def get_coins(self):
        return self._coins

    def open_bank(self, code):
        if code == self.__secret_code:
            print(f"Bank opened! You have {self._coins} coins!")
        else:
            print("Wrong code! Bank stays locked!")

bank = PiggyBank()
bank.add_coin()
bank.add_coin()
bank.add_coin()
print(f"Coins: {bank.get_coins()}")
bank.open_bank(1234)
bank.open_bank(9999)
```

**Output:**
```
Added a coin! Total: 1
Added a coin! Total: 2
Added a coin! Total: 3
Coins: 3
Bank opened! You have 3 coins!
Wrong code! Bank stays locked!
```

Instead of changing `_coins` directly, outside code uses `add_coin()` and `get_coins()`. This lets the class control *how* its data is accessed and modified.

## Abstraction

**Abstraction** means hiding complex details and showing only the essential interface. While encapsulation hides *data*, abstraction hides *complexity*. You use something through a simple interface without needing to understand what happens inside.

In Python, you can create **abstract classes** using the `abc` module. An abstract class defines methods that every child class *must* implement, without providing the implementation itself:

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass          # No implementation — child classes must provide one

    @abstractmethod
    def describe(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def describe(self):
        print(f"Rectangle: {self.width} x {self.height}, area = {self.area()}")

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14159 * self.radius ** 2

    def describe(self):
        print(f"Circle: radius {self.radius}, area = {self.area():.2f}")

# shape = Shape()  # This would cause an error — you can't create an abstract class!

shapes = [Rectangle(4, 5), Circle(3), Rectangle(10, 2)]
for shape in shapes:
    shape.describe()
```

**Output:**
```
Rectangle: 4 x 5, area = 20
Circle: radius 3, area = 28.27
Rectangle: 10 x 2, area = 20
```

The `Shape` class says "every shape must have an `area()` and `describe()` method" but doesn't say *how*. Each child class fills in the details. This also demonstrates polymorphism — we loop through different shapes and call `describe()` on each one.

For beginners, the key takeaway is: abstraction means **providing simple interfaces that hide complexity**. You'll see this in action when using Turtle and Pygame — you call methods like `forward()` or `draw()` without needing to know how pixels are rendered on screen.

Try it yourself! Create a `Vehicle` parent class with a `move()` method, then create `Car` and `Bicycle` child classes that override `move()` with their own messages. Put them in a list and loop through it.

---

## Navigation

⬅️ **[Previous: Chapter 2 - Classes and Objects](chapter-02.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 4 - Importing Your Own Code](chapter-04.md)**
