---
layout: default
title: Chapter 10 - Common Mistakes and Next Steps
---

# Chapter 10: Common Mistakes and Next Steps

## Common Mistakes Among Beginners

Here are some of the most frequent mistakes that beginners make. Knowing about them ahead of time can save you a lot of debugging!

### Single `=` vs. Double `==`

This is the most common mix-up for new programmers:

- **`=`** is the **assignment** operator — it puts a value into a variable.
- **`==`** is the **comparison** operator — it checks whether two values are equal.

```python
x = 5       # Assigns the value 5 to x
x == 5      # Checks if x equals 5 (True)
```

If you accidentally use `=` inside an if-statement, Python will give you an error:

```python
# Wrong:
if x = 5:     # SyntaxError!

# Correct:
if x == 5:    # This works
    print("x is five")
```

### Forgetting the `:` and Indentation

Python uses `:` at the end of lines that start a block (if-statements, loops, functions), and **indentation** to mark what's inside that block. Forgetting either one causes an error:

```python
# Wrong — missing colon:
if x > 5
    print("big")

# Wrong — missing indentation:
if x > 5:
print("big")

# Correct:
if x > 5:
    print("big")
```

This applies to `if`, `elif`, `else`, `for`, `while`, `def`, and more.

### Modifying a List While Looping Through It

Removing items from a list while you're looping through it can cause unexpected behavior because the indices shift as items are removed:

```python
# Wrong — may skip items or cause errors:
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    if num % 2 == 0:
        numbers.remove(num)

# Better — build a new list:
numbers = [1, 2, 3, 4, 5]
odds = []
for num in numbers:
    if num % 2 != 0:
        odds.append(num)
print(odds)  # [1, 3, 5]
```

### Off-by-One Errors

Remember that indices start at **0**, and `range(n)` goes from 0 to `n-1` (not `n`). Slicing with `[start:end]` includes `start` but **excludes** `end`. This is the most common source of "off-by-one" bugs:

```python
my_list = ["a", "b", "c", "d"]
print(my_list[4])      # IndexError! Valid indices are 0, 1, 2, 3
print(my_list[0:2])    # ['a', 'b'] — NOT ['a', 'b', 'c']
```

### Forgetting to Convert Types

`input()` always returns a string. If you want to do math with user input, you must convert it first:

```python
# Wrong — this concatenates strings, not adds numbers:
age = input("Age: ")
print(age + 1)  # TypeError!

# Correct:
age = int(input("Age: "))
print(age + 1)  # Works!
```

### Using a Variable Before Defining It

Python reads code from top to bottom. If you try to use a variable before assigning a value to it, you'll get a `NameError`:

```python
print(x)  # NameError: name 'x' is not defined
x = 5
```

Always make sure a variable is defined *before* the line that uses it.

## Next Steps

Congratulations — you've learned the fundamentals of Python! Here's what you can do next:

**Build something fun:** Try making a simple game (number guessing, rock-paper-scissors, quiz game), a calculator, or a program that generates random stories.

**Learn Object-Oriented Programming:** The next guide in this series, [Object-Oriented Programming for Python with Turtle and Pygame](../Python-OOP-Turtle-Pygame/table-of-contents.md), covers classes, objects, and building graphical programs.

Happy coding!

---

## Navigation

⬅️ **[Previous: Chapter 9 - Useful Built-in Functions and Libraries](chapter-09.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

🎉 **You've completed the Intro to Python Guide!**
