---
layout: default
title: Chapter 1 - Introduction to OOP
---

# Chapter 1: Introduction to Object-Oriented Programming (OOP)

## Why OOP?

Imagine you're building an animal simulator game. You need dogs, cats, and birds — each with its own name, age, favorite food, and behaviors like eating or playing. Without OOP, you might write separate variables and functions for every single animal, and the code would get messy fast.

**Object-oriented programming** (OOP) is a way of organizing code by grouping related data and actions together into reusable building blocks. It's one of the most widely used approaches in professional software development, and it's how Python's own built-in types (strings, lists, dictionaries) are built under the hood.

## The Cookie Cutter Analogy

The core idea of OOP comes down to two things: **classes** and **objects**.

Think of a **class** as a cookie cutter. It defines the shape — what every cookie will look like. But the cookie cutter itself isn't a cookie. An **object** is an actual cookie made from that cutter. You can make as many cookies (objects) as you want from the same cutter (class), and each cookie can be decorated differently (have different data).

In Python terms: a class defines *what* something is (its data and behaviors), and an object is a *specific instance* of that class with actual values.

## A First Taste

Here's a tiny example to show what this looks like in code. Don't worry about understanding every detail yet — we'll break it all down in Chapter 2.

```python
class Pet:
    def __init__(self, name, animal_type):
        self.name = name
        self.animal_type = animal_type

    def greet(self):
        print(f"Hi! I'm {self.name} the {self.animal_type}.")

# Create two pet objects from the same class
buddy = Pet("Buddy", "dog")
whiskers = Pet("Whiskers", "cat")

buddy.greet()
whiskers.greet()
```

**Output:**
```
Hi! I'm Buddy the dog.
Hi! I'm Whiskers the cat.
```

Notice how we wrote the `Pet` class once, then created two different pets from it — each with its own name and type. That's the power of OOP: **define once, use many times**.

## What's Ahead

OOP has a few new ideas to learn, so we'll take them one step at a time:

- **Chapter 2**: Classes and objects — the building blocks
- **Chapter 3**: OOP principles — inheritance, polymorphism, encapsulation, and abstraction
- **Chapter 4**: Importing code across files
- **Chapter 5**: Turtle graphics — drawing with OOP
- **Chapter 6**: Pygame — building games with OOP

Let's get started!

---

## Navigation

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 2 - Classes and Objects](chapter-02.md)**
