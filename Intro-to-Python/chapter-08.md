---
layout: default
title: Chapter 8 - Functions
---

# Chapter 8: Functions

If you've studied algebra, you may be familiar with **functions** — they take an input, do something with it, and produce an output:

```
f(x) = x + 6
g(x, y) = x + 2y

f(5) = 11
f(8) = 14
g(5, 3) = 11
g(13, 17) = 47
```

Python functions work the same way: they take inputs, run a consistent set of steps, and (optionally) return an output. Functions let you **reuse** code instead of writing the same thing over and over. If you've used the "My Blocks" feature in Scratch, you already know the idea — functions are custom blocks that you define once and use anywhere.

## Function Structure

To create a function, you **define** it with the `def` keyword:

```python
def add_six(x):
    result = x + 6
    return result
```

A function definition has three parts:

1. **Header**: `def function_name(parameters):` — the name and what inputs it takes
2. **Body**: the indented code that runs when the function is called
3. **Return statement**: `return value` — the output that the function sends back

### Parameters and Arguments

The variables listed in the function definition are called **parameters**. The actual values you pass in when calling the function are called **arguments**.

```python
def greet(name):    # "name" is the parameter
    print(f"Hello, {name}!")

greet("Alice")      # "Alice" is the argument
greet("Bob")        # "Bob" is the argument
```

**Output:**
```
Hello, Alice!
Hello, Bob!
```

A function can have multiple parameters, or no parameters at all:

```python
def add(a, b):
    return a + b

def say_hi():
    print("Hi!")
```

### Return Statement

The `return` keyword sends a value back to wherever the function was called. Once Python reaches a `return` statement, it **immediately exits** the function — any code after it is skipped.

```python
def add_six(x):
    return x + 6

result = add_six(5)
print(result)         # 11
print(add_six(8))     # 14
```

A function can return multiple values, separated by commas. These come back as a **tuple**:

```python
def min_and_max(a, b, c):
    return min(a, b, c), max(a, b, c)

smallest, largest = min_and_max(5, 2, 8)
print(smallest, largest)  # 2 8
```

## Calling Functions

When you **call** a function, you write its name followed by the arguments in parentheses. The return value can be stored in a variable or used directly:

```python
def add_2y(x, y):
    return x + 2 * y

# Store the result in a variable
answer = add_2y(5, 3)
print(answer)        # 11

# Use the result directly
print(add_2y(13, 17))  # 47
```

Here's a more interesting example — a function that solves quadratic equations using the quadratic formula $x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$:

```python
def solve_quadratic(a, b, c):
    discriminant = b**2 - 4*a*c
    if discriminant < 0:
        return None, None  # No real solutions
    root1 = (-b + discriminant ** 0.5) / (2 * a)
    root2 = (-b - discriminant ** 0.5) / (2 * a)
    return root1, root2

x1, x2 = solve_quadratic(1, -3, 2)
print("Solutions:", x1, x2)  # Solutions: 2.0 1.0
```

## Void Functions

Functions without a `return` statement are called **void functions**. They perform an action (like printing) but don't send a value back. If you try to capture the return value anyway, you'll get `None`.

```python
def introduce(name, age):
    print(f"Hello, my name is {name}.")
    if age >= 18:
        print("I can drive a car.")
        return  # Exits the function early (returns None)
    if age >= 16:
        print("I can drive under supervision.")
        return
    print("I can't drive yet.")

introduce("Andrew", 25)
result = introduce("Brian", 17)
print(result)
```

**Output:**
```
Hello, my name is Andrew.
I can drive a car.
Hello, my name is Brian.
I can drive under supervision.
None
```

## Default Parameter Values

You can give parameters **default values** so they become optional when calling the function:

```python
def greet(name, greeting="Hello"):
    print(f"{greeting}, {name}!")

greet("Alice")              # Uses default: "Hello, Alice!"
greet("Alice", "Goodbye")   # Override: "Goodbye, Alice!"
greet("Bob", "Hey")         # Override: "Hey, Bob!"
```

**Output:**
```
Hello, Alice!
Goodbye, Alice!
Hey, Bob!
```

Parameters with default values must come **after** parameters without defaults.

## Variable Scope

Variables created inside a function are **local** — they only exist within that function and disappear when the function ends. Variables created outside functions are accessible everywhere, but modifying them inside a function requires special care.

```python
def my_function():
    secret = "I only exist inside this function"
    print(secret)

my_function()

# This would cause an error:
# print(secret)  # NameError: name 'secret' is not defined
```

This means you can safely use the same variable name in different functions without them interfering with each other:

```python
def function_a():
    x = 10
    print("A:", x)

def function_b():
    x = 20
    print("B:", x)

function_a()  # A: 10
function_b()  # B: 20
```

The `x` in `function_a` and the `x` in `function_b` are completely separate variables.

---

## Navigation

⬅️ **[Previous: Chapter 7 - Tuples, Dictionaries, and Sets](chapter-07.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 9 - Useful Built-in Functions and Libraries](chapter-09.md)**
