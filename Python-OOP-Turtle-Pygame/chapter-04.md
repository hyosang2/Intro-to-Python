---
layout: default
title: Chapter 4 - Importing Your Own Code
---

# Chapter 4: `import` and Cross-File Programming

When Python programs grow larger, keeping everything in one file becomes hard to manage. The **`import`** statement lets you use code from other Python files and libraries, which is especially useful when you have many classes.

## Import Methods

There are several ways to import modules in Python:

```python
# Method 1: Import the entire module
import math
print(math.sqrt(25))  # 5.0
print(math.pi)        # 3.14159...

# Method 2: Import specific items
from math import sqrt, pi
print(sqrt(25))       # 5.0
print(pi)             # 3.14159...

# Method 3: Import with a nickname (alias)
import random as r
print(r.randint(1, 10))

# Method 4: Import everything (not recommended — makes it unclear where things come from)
from math import *
```

For a detailed reference on built-in libraries like `random`, `math`, and `time`, see [Chapter 9 of the Intro to Python guide](../Intro-to-Python/chapter-09.md).

## Importing Your Own Files

This is where imports become essential for OOP. When you have classes in separate files, you import them just like libraries — using the filename without the `.py` extension.

Imagine you have two files in the same folder:

**`pet.py`** — contains the Pet class:
```python
class Pet:
    def __init__(self, name, animal_type):
        self.name = name
        self.animal_type = animal_type

    def speak(self):
        print(f"{self.name} the {self.animal_type} says hello!")

    def __str__(self):
        return f"{self.name} the {self.animal_type}"
```

**`main.py`** — your main program:
```python
from pet import Pet

buddy = Pet("Buddy", "dog")
buddy.speak()
print(buddy)
```

**Output:**
```
Buddy the dog says hello!
Buddy the dog
```

You can also import multiple classes from the same file:

```python
# If pet.py also contained a Toy class:
from pet import Pet, Toy
```

Or import the whole file as a module:

```python
import pet

buddy = pet.Pet("Buddy", "dog")
```

### Why Organize Code This Way?

As your programs grow, separating classes into their own files keeps things organized. A typical project structure might look like:

```
my_game/
    main.py          ← runs the game
    player.py        ← Player class
    enemy.py         ← Enemy class
    item.py          ← Item class
```

Each file focuses on one class (or a group of related classes), and `main.py` imports what it needs. This makes code easier to read, debug, and work on with others.

## Documentation

Every good Python library comes with **documentation** that explains how to use its classes and functions. Reading documentation is an essential skill.

Key places to find Python documentation:

- Official Python docs: [docs.python.org](https://docs.python.org/)
- Library-specific websites (e.g., [pygame.org](https://pygame.org))
- The `help()` function in the Python interpreter

```python
import math
help(math.sqrt)   # Shows documentation for sqrt
help(print)        # Shows how to use print
```

### `sys` and `os`

Two useful built-in libraries for working with the file system:

**`sys`** provides system-specific information:
```python
import sys
print("Python version:", sys.version)
print("Platform:", sys.platform)
```

**`os`** lets you interact with the operating system:
```python
import os
print("Current folder:", os.getcwd())
print("Files here:", os.listdir("."))
print("Does 'test.txt' exist?", os.path.exists("test.txt"))
```

These become handy when your program needs to find files, check paths, or work across different computers.

Try it yourself! Create two files: `animal.py` with an `Animal` class, and `main.py` that imports `Animal`, creates a few objects, and prints them.

---

## Navigation

⬅️ **[Previous: Chapter 3 - OOP Principles](chapter-03.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 5 - Turtle Graphics](chapter-05.md)**
