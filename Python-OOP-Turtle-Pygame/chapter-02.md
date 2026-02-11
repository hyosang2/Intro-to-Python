---
layout: default
title: Chapter 2 - Classes and Objects
---

# Chapter 2: Classes and Objects

A **class** is a blueprint for creating objects. An **object** is a specific thing created from that blueprint. To use OOP, you first *define* a class (the blueprint), then *instantiate* objects from it (the things). This is similar to how you define a function first, then call it — but at a larger scale.

A class starts with a header:

```python
class ClassName:
```

Unlike variable or function names, class names capitalize each word and do **not** use underscores. For example: `Pet`, `SpaceShip`, `GameCharacter`.

A class can contain **variables** (data) and **methods** (functions that belong to the class). Let's build one up piece by piece.

## The `__init__()` Method

The **`__init__()`** method (also called the **constructor**) is a special function that runs automatically when you create a new object from a class. It sets up the object's starting data. A class should have exactly one `__init__()` method.

```python
def __init__(self, name, age):
```

The first parameter, **`self`**, refers to the specific object being created. Python fills it in automatically — you never pass it yourself. The remaining parameters (`name`, `age`) are values you provide when creating the object.

## Instance Variables

**Instance variables** are data that belong to a specific object. Each object gets its own copy. You create them inside `__init__()` using the `self.` prefix:

```python
class Pet:
    def __init__(self, name, age, animal_type, favorite_food):
        self.name = name
        self.age = age
        self.animal_type = animal_type
        self.favorite_food = favorite_food
        print(f"{self.name} is a {self.age} year old {self.animal_type} who loves {self.favorite_food}!")
```

Here, `self.name`, `self.age`, `self.animal_type`, and `self.favorite_food` are all instance variables. When you create different Pet objects, each one will have its own values for these variables.

## Class Variables

**Class variables** are shared by *all* objects created from the class. They're defined outside of any method, directly inside the class body.

```python
class Pet:
    pet_count = 0  # Class variable — shared by all Pet objects

    def __init__(self, name, age, animal_type, favorite_food):
        self.name = name                # Instance variable — unique to each Pet
        self.age = age
        self.animal_type = animal_type
        self.favorite_food = favorite_food

        print(f"{self.name} is a {self.age} year old {self.animal_type} who loves {self.favorite_food}!")
        Pet.pet_count += 1              # Update the shared count
```

Notice the difference: instance variables use **`self.`** (unique to each object), while class variables use the **class name** as a prefix (e.g., `Pet.pet_count`).

## Creating Objects (Instantiation)

To create an object, call the class name like a function, passing the values that `__init__()` expects (minus `self`):

```python
buddy = Pet("Buddy", 3, "dog", "chicken")
whiskers = Pet("Whiskers", 5, "cat", "tuna")

print(f"Total pets: {Pet.pet_count}")
print(f"{buddy.name} is {buddy.age} years old")
print(f"{whiskers.name} is {whiskers.age} years old")
```

**Output:**
```
Buddy is a 3 year old dog who loves chicken!
Whiskers is a 5 year old cat who loves tuna!
Total pets: 2
Buddy is 3 years old
Whiskers is 5 years old
```

Creating an object is formally called **instantiation** — you're creating an *instance* of the class. Each instance has its own copy of the instance variables but shares the class variable `pet_count`.

Outside the class, you access instance variables with the **object name** (e.g., `buddy.name`) and class variables with the **class name** (e.g., `Pet.pet_count`).

## Instance Methods

**Instance methods** are functions defined inside a class that operate on a specific object. They always take `self` as their first parameter, which gives them access to that object's instance variables. While instance variables represent the **characteristics** of an object, instance methods represent its **behaviors**.

```python
class Pet:
    pet_count = 0

    def __init__(self, name, age, animal_type, favorite_food):
        self.name = name
        self.age = age
        self.animal_type = animal_type
        self.favorite_food = favorite_food
        Pet.pet_count += 1

    def play(self):
        if self.age < 5:
            print(f"{self.name} is playing happily!")
        else:
            print(f"{self.name} is taking a nap.")

    def eat(self, food):
        if food == self.favorite_food:
            print(f"{self.name} loves eating {food}!")
        else:
            print(f"{self.name} doesn't really like {food}.")

buddy = Pet("Buddy", 3, "dog", "chicken")
buddy.play()
buddy.eat("chicken")
buddy.eat("broccoli")
```

**Output:**
```
Buddy is playing happily!
Buddy loves eating chicken!
Buddy doesn't really like broccoli.
```

The `play` method takes no extra parameters (just `self`), while `eat` takes a `food` parameter. Both use `self.` to access the object's own data. When you call `buddy.play()`, Python automatically passes `buddy` as `self`.

## The `__str__()` Method

When you `print()` an object, Python doesn't know how to display it nicely by default. The special **`__str__()`** method lets you define what string should appear:

```python
class Pet:
    def __init__(self, name, age, animal_type):
        self.name = name
        self.age = age
        self.animal_type = animal_type

    def __str__(self):
        return f"{self.name} the {self.animal_type} (age {self.age})"

buddy = Pet("Buddy", 3, "dog")
print(buddy)
```

**Output:**
```
Buddy the dog (age 3)
```

Without `__str__()`, printing an object would show something unhelpful like `<__main__.Pet object at 0x7f...>`. Defining `__str__()` makes your objects much easier to work with and debug.

## Objects as Variables

Since classes act like custom data types, objects can be used anywhere variables can — including in lists, as function arguments, or as return values:

```python
class Toy:
    def __init__(self, name, color):
        self.name = name
        self.color = color

    def play_with(self):
        print(f"Playing with the {self.color} {self.name}!")

    def __str__(self):
        return f"{self.color} {self.name}"

# Create toy objects and put them in a list
teddy = Toy("teddy bear", "brown")
ball = Toy("ball", "red")
robot = Toy("robot", "blue")

toy_box = [teddy, ball, robot]

# Loop through the list and call methods on each object
for toy in toy_box:
    toy.play_with()

print(f"I have {len(toy_box)} toys: {', '.join(str(t) for t in toy_box)}")
```

**Output:**
```
Playing with the brown teddy bear!
Playing with the red ball!
Playing with the blue robot!
I have 3 toys: brown teddy bear, red ball, blue robot
```

Understanding that objects are just like variables is key to using OOP effectively. You'll see this idea everywhere in the Turtle and Pygame chapters.

## Access Reference

Here's a quick reference for how to access class members from different places:

| **Where you are** | **Class variable** | **Instance variable** | **Instance method** |
|---|---|---|---|
| Inside an instance method | `ClassName.var` | `self.var` | `self.method()` |
| Outside the class | `ClassName.var` | `object_name.var` | `object_name.method()` |

Try it yourself! Create a `Student` class with a name, grade, and a method `introduce()` that prints a greeting. Then create three students and store them in a list.

---

## Navigation

⬅️ **[Previous: Chapter 1 - Introduction to OOP](chapter-01.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 3 - OOP Principles](chapter-03.md)**
