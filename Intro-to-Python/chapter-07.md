---
layout: default
title: Chapter 7 - More Tips for Python
---

# Chapter 7: More Tips for Python

## More Built-in Functions

We have learned about "freelance" built-in functions like `print()` and `range()`. Below are more essential built-in functions for Python programming.

### `input()`

`input()` allows the user to insert a piece of text as input to the program, which is perceived as a string. It is helpful for building programs that need user interaction. It takes one string argument to be displayed as an instruction for the user, where the user input is formed in the same line as the instruction.

```python
user_input = input("Type your name: ")
print("Hello, " + user_input + "!")
```

**Output:**
```
Type your name: Gary
Hello, Gary!
```

Note that "Gary" is typed by the user while running the code.

## Libraries

**Libraries** offer functions and classes (object-oriented programming will be covered in the next guide) to simplify coding. However, to utilize these tools, the relevant library must be **imported**. For most cases, the import statements are placed at the beginning of the file to enable the subsequent lines of the file to access the library.

```python
import <library_name>
...
<library_name>.<function_name>()
```

where `<library_name>` is replaced by the name of the library that contains the desired function.

This guide introduces three Python libraries, emphasizing the use of their imported functions and other properties. However, please note that the listed library properties are not exhaustive, so it's recommended to explore other methods available within the libraries for further learning.

### `random`

`random` library offers tools for actions that relate to random selections. Below are a few examples of functions from `random`:

- **`random.randint(start: int, end: int)`** returns an integer randomly selected from the range between the `start` and `end`, inclusive.
- **`random.choice(list: List)`** returns an element randomly selected from `list`. This method works on tuples, but for dictionaries, `keys()`, `values()`, or `items()` should be used to convert into iterable sequences before using the method.

```python
import random

print(random.randint(1, 10))

my_list = ["a", "c", "e"]
print(random.choice(my_list))
```

**Output:**
```
1
a
```

where each rerun of above will result in different outputs.

### `math`

`math` library has tools that do mathematical operations that can't be done with Python's built-in methods. Below are a few examples of functions and constants from `math`:

- **`math.sqrt(num: int/float)`** returns the square root of `num` in float.
- **`math.inf`** is a float constant representing infinity.
- **`math.pi`** returns the float constant of π.

```python
import math

print(math.sqrt(16))
print(math.sqrt(10.6))

print(math.inf)
if math.inf > 1e32:
    print("Greater")

print(math.pi)
```

**Output:**
```
4.0
3.255764119219941
inf
Greater
3.141592653589793
```

### `time`

Python's `time` module provides tools to provide information related to time.

- **`time.time()`** Returns current time in seconds in float since the epoch. In Unix systems, the epoch is set at January 1, 1970, 00:00:00 UTC.
- **`time.ctime(time: int/float)`** Converts the seconds since epoch like the one above into the format `Day Mon DD HH:MM:SS Year`.
- **`time.sleep(second: int/float)`** Holds the code from continuing for the set seconds.

```python
import time

curr_time = time.time()
print(curr_time, type(curr_time))

date_time = time.ctime(curr_time)
print(date_time, type(date_time))

time.sleep(5)
# Below code runs 5 seconds later.
print("Hi! It's been 5 seconds!")
```

**Output:**
```
1744389965.6022182 <class 'float'>
Fri Apr 11 16:46:05 2025 <class 'str'>
Hi! It's been 5 seconds!
```

## Common Mistakes Among Beginners

Here are some common mistakes that beginners make which lead to errors or conflicts from code reviews.

### Single vs Double `=`

While both symbols have similar implications, misusing them will lead to compilation errors. My advice for understanding the differences is to remember that:

- **`=`** **assigns** right-hand-side to left-hand-side. The value on the right-hand-side of `=` is saved to the variable specified on the left-hand-side.
- **`==`** **compares** left-hand-side to right-hand-side. The compiler checks whether the represented values on the left-hand-side and right-hand-side are equal.

### `:` and Indentation

Python, an indentation-centric programming language, differs from other languages in that its function and if-statement bodies are not enclosed in brackets that serve as markers. Instead, Python uses indentation to indicate the boundaries of these blocks. Fortunately, if you've been following the indentation pattern in other languages, you'll find a similar pattern in Python.

Notice the `:` at the end of if-statements, else syntax, while and for-loop headers, and function headers. This marker indicates the beginning of the body, which should be encapsulated via indentation.

---

## Navigation

⬅️ **[Previous: Chapter 6 - Functions](chapter-06.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

🎉 **You've completed the Intro to Python Guide!**