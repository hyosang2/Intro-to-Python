---
layout: default
title: Chapter 3 - Objects
---

# Chapter 3: Objects

## Object Creation (Instantiation)

Chapter 2 briefly explored an example of object creation. The formal term for object creation is called **instantiation**. Instantiation means creating an *instance* of a class, which, in this context, refers to an object.

Like how we call a function using the parameters fed in the same order as corresponding arguments, instantiating an object requires the same order of parameters as the arguments required by the `__init__()` method of the class.

## Classes as Data Types, Objects as Variables

From the Intro to Python guide, we learned about **primitive data types** that contain a single piece of data, such as integers, floats, and Boolean. We also learned **non-primitive data types**, such as strings, contain multiple pieces of data. They also include lists, dictionaries, and other kinds of data structures.

Both categories of data types are defined using classes, and the variables created with such types are objects. In other words, classes can be viewed as "custom data types".

What does this mean? **Classes can be cared like data types, and objects can be cared like variables**. For example, lists in Python contain items consisting of data of a certain type, or a mix of data from different data types. This includes objects created from custom classes.

```python
class Toy:
    def __init__(self, name, color, size):
        self.name = name
        self.color = color
        self.size = size
        print(f"Created a {self.color} {self.name} that is {self.size} size!")
    
    def play_with(self):
        print(f"Playing with the {self.color} {self.name}!")

# Create toy objects
teddy = Toy("teddy bear", "brown", "large")
ball = Toy("ball", "red", "small")
robot = Toy("robot", "blue", "medium")

# Put toys in a list and play with each one
toy_box = [teddy, ball, robot]
for toy in toy_box:
    toy.play_with()
```

**Output:**
```
Created a brown teddy bear that is large size!
Created a red ball that is small size!
Created a blue robot that is medium size!
Playing with the brown teddy bear!
Playing with the red ball!
Playing with the blue robot!
```

Understanding classes as data types and objects as variables will significantly enhance your comprehension of OOP. This concept becomes especially important when we explore the principles of OOP in Chapter 4, and when we apply these concepts to graphics programming with Turtle (Chapter 6) and game development with Pygame (Chapter 7).

---

## Navigation

⬅️ **[Previous: Chapter 2 - Classes](chapter-02.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 4 - OOP Principles](chapter-04.md)**