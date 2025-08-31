---
layout: default
title: Chapter 5 - Import and Modules
---

# Chapter 5: `import` and Cross-File Programming

When Python programs become complex, organizing code across multiple files becomes essential. This is especially important when working with object-oriented programs that may have many classes, as introduced in Chapter 2. The `import` statement allows you to use code from other Python files and libraries.

## `import` Methods

There are several ways to import modules in Python:

```python
# Method 1: Import entire module
import math
print(math.sqrt(25))  # Output: 5.0
print(math.pi)        # Output: 3.141592653589793

# Method 2: Import specific functions
from math import sqrt, pi
print(sqrt(25))  # Output: 5.0
print(pi)        # Output: 3.141592653589793

# Method 3: Import with alias (nickname)
import random as r
print(r.randint(1, 10))  # Random number between 1 and 10

# Method 4: Import everything (not recommended)
from math import *
print(sqrt(25))  # Output: 5.0
```

**Output:**
```
5.0
3.141592653589793
5.0
3.141592653589793
7
5.0
```

To import your own Python files, simply use the filename without the `.py` extension:

```python
# If you have a file called "my_games.py"
from my_games import GuessGame, DiceGame

# Or import the entire file
import my_games
game = my_games.GuessGame()
```

## Libraries Continued

Python's strength lies in its vast ecosystem of libraries. Libraries are collections of pre-written code that solve common programming problems.

### Documentations

Every good Python library comes with **documentation** that explains how to use its functions and classes. Reading documentation is a crucial skill for programmers.

Key places to find Python documentation:
- Official Python docs: `https://docs.python.org/`
- Library-specific websites (e.g., `pygame.org`)
- `help()` function in Python interpreter

```python
import math
help(math.sqrt)  # Shows documentation for sqrt function

# You can also get help on any function
help(print)      # Shows how to use print function
```

### `sys` and `os`

Two important built-in libraries for system operations:

**`sys`** - System-specific parameters and functions:
```python
import sys

print("Python version:", sys.version)    # Python version info
print("Platform:", sys.platform)         # Your computer type
print("Path:", sys.path[0])              # Where Python looks for files
```

**Output:**
```
Python version: 3.9.7 (default, Sep 16 2021, 08:50:36) 
Platform: darwin
Path: /Users/student/python_projects
```

**`os`** - Operating system interface:
```python
import os

print("Current folder:", os.getcwd())         # Where you are now
print("Files here:", os.listdir("."))         # List files in current folder
print("Does 'test.txt' exist?", os.path.exists("test.txt"))  # Check if file exists

# Create a new folder (be careful!)
# os.mkdir("my_new_folder")
```

**Output:**
```
Current folder: /Users/student/python_projects
Files here: ['main.py', 'my_game.py', 'README.txt']
Does 'test.txt' exist? False
```

Here's a fun example using `random` for a simple guessing game:

```python
import random

# Simple number guessing game
secret_number = random.randint(1, 10)
print("I'm thinking of a number between 1 and 10!")

guess = int(input("What's your guess? "))
if guess == secret_number:
    print("You got it! Great job!")
else:
    print(f"Sorry! The number was {secret_number}. Try again!")
```

**Output:**
```
I'm thinking of a number between 1 and 10!
What's your guess? 7
Sorry! The number was 3. Try again!
```

Now that you know how to import libraries and use different Python modules, you're ready to explore more exciting programming! The next sections will show you how to create visual programs that draw pictures and games on the screen using the OOP concepts from Chapters 2 through 4. We'll start with Turtle graphics in Chapter 6, then advance to game development with Pygame in Chapter 7.

---

## Navigation

⬅️ **[Previous: Chapter 4 - OOP Principles](chapter-04.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 6 - Turtle Graphics](chapter-06.md)**