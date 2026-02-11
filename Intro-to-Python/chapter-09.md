---
layout: default
title: Chapter 9 - Useful Built-in Functions and Libraries
---

# Chapter 9: Useful Built-in Functions and Libraries

Python comes with many built-in functions beyond `print()`, `len()`, and `range()`. This chapter covers the ones you'll use most often, plus three helpful **libraries** that extend Python's capabilities.

## Essential Built-in Functions

### `abs()` — Absolute Value

`abs()` returns the absolute value of a number (its distance from zero, always positive):

```python
print(abs(-5))     # 5
print(abs(5))      # 5
print(abs(-3.14))  # 3.14
```

This is especially useful when you want to find how far apart two numbers are, regardless of order:

```python
a = 10
b = 3
distance = abs(a - b)
print(distance)  # 7
```

### `max()` and `min()` — Largest and Smallest

`max()` returns the largest value and `min()` returns the smallest. They work with individual values or with lists:

```python
print(max(3, 7, 2))       # 7
print(min(3, 7, 2))       # 2

scores = [85, 92, 78, 95, 88]
print(max(scores))        # 95
print(min(scores))        # 78
```

### `sum()` — Add Up a Collection

`sum()` adds up all the numbers in a list (or other iterable):

```python
numbers = [1, 2, 3, 4, 5]
print(sum(numbers))  # 15

# Combine with len() to find the average
average = sum(numbers) / len(numbers)
print(average)  # 3.0
```

### `sorted()` — Sort Without Changing the Original

We saw `sorted()` in the lists chapter. As a reminder, it returns a **new** sorted list and leaves the original unchanged:

```python
names = ["Charlie", "Alice", "Bob"]
print(sorted(names))   # ['Alice', 'Bob', 'Charlie']
print(names)            # ['Charlie', 'Alice', 'Bob'] — unchanged
```

### `round()` — Round a Number

`round()` rounds a float to a given number of decimal places (default is 0):

```python
print(round(3.14159))       # 3
print(round(3.14159, 2))    # 3.14
print(round(2.5))           # 2 (Python uses "banker's rounding")
```

### Quick Reference Table

| Function | What it does | Example |
|----------|-------------|---------|
| `abs(x)` | Absolute value | `abs(-5)` → `5` |
| `max(...)` | Largest value | `max(3, 7, 2)` → `7` |
| `min(...)` | Smallest value | `min(3, 7, 2)` → `2` |
| `sum(list)` | Sum of all items | `sum([1,2,3])` → `6` |
| `sorted(list)` | New sorted list | `sorted([3,1,2])` → `[1,2,3]` |
| `round(x, n)` | Round to `n` decimals | `round(3.14, 1)` → `3.1` |
| `len(x)` | Length/count | `len("Hi")` → `2` |
| `type(x)` | Data type | `type(5)` → `<class 'int'>` |
| `int(x)` | Convert to integer | `int("5")` → `5` |
| `float(x)` | Convert to float | `float("3.14")` → `3.14` |
| `str(x)` | Convert to string | `str(42)` → `"42"` |
| `bool(x)` | Convert to Boolean | `bool(0)` → `False` |
| `input(prompt)` | Read user input | `input("Name? ")` → string |

## Libraries

**Libraries** provide extra functions and tools that aren't built into Python by default. To use a library, you need to **import** it — usually at the top of your file:

```python
import library_name

library_name.function_name()
```

Here are three commonly used libraries.

### `random` — Random Numbers and Choices

The `random` library lets you work with random values:

- **`random.randint(a, b)`** returns a random integer from `a` to `b`, inclusive.
- **`random.choice(sequence)`** picks a random item from a list, tuple, or string.

```python
import random

print(random.randint(1, 10))   # Random number from 1 to 10

my_list = ["apple", "banana", "cherry"]
print(random.choice(my_list))  # Random item from the list
```

Each time you run the code, you may get different results.

Note: `random.choice()` needs a **sequence** (something with a length and indexes, like a list or string). To pick a random key from a dictionary, convert the keys to a list first:

```python
scores = {"Alice": 95, "Bob": 87}
random_name = random.choice(list(scores.keys()))
```

### `math` — Mathematical Operations

The `math` library provides math functions and constants beyond basic arithmetic:

- **`math.sqrt(x)`** returns the square root of `x`.
- **`math.pi`** is the constant $\pi$ (approximately 3.14159).
- **`math.inf`** represents infinity.

```python
import math

print(math.sqrt(16))      # 4.0
print(math.sqrt(10.6))    # 3.255...
print(math.pi)            # 3.141592653589793

if math.inf > 1000000:
    print("Infinity is bigger!")  # This will print
```

### `time` — Working with Time

The `time` library provides tools for tracking and controlling time:

- **`time.time()`** returns the current time in seconds (since January 1, 1970).
- **`time.ctime(seconds)`** converts seconds into a readable date-time string.
- **`time.sleep(seconds)`** pauses the program for the given number of seconds.

```python
import time

current = time.time()
print(current)             # Something like 1744389965.6

print(time.ctime(current)) # Something like "Fri Apr 11 16:46:05 2025"

print("Wait for it...")
time.sleep(3)
print("3 seconds later!")
```

These libraries only scratch the surface — Python has hundreds of libraries for everything from web development to data science. You can always search online for "Python [topic] library" to find the right tool.

---

## Navigation

⬅️ **[Previous: Chapter 8 - Functions](chapter-08.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 10 - Common Mistakes and Next Steps](chapter-10.md)**
