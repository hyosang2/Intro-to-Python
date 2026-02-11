---
layout: default
title: Chapter 2 - Variables and Data Types
---

# Chapter 2: Variables and Data Types

A **variable** is like a labeled box that stores a value. You give the box a name, put something inside it, and can look at or change what's inside later. It's similar to the "set my variable to" block in Scratch.

```python
x = 7
y = "Hello World!"

print(x)
print(y)
```

**Output:**
```
7
Hello World!
```

In the code above, the `=` sign **assigns** the value on the right side to the variable name on the left side. After these lines, `x` holds the value `7` and `y` holds the value `"Hello World!"`.

### Naming Variables

By convention, variable names use lowercase letters and numbers, separated by underscores (`_`). For example: `my_score`, `player_name`, `total_count`. **Names that use characters other than letters, numbers, and underscores — or that start with a number — are not allowed.**

## Data Types

Python has several **data types** — different kinds of values that variables can hold:

```python
location = "Pasadena, CA"   # String
x = 7                       # Integer
y = 3.14                    # Float
is_daytime = True           # Boolean
```

Here's what each type means:

- **Strings** are text — a group of characters like letters, numbers, and punctuation. You create a string by putting text inside quotation marks (single `'...'` or double `"..."`).

- **Integers** are whole numbers, both positive and negative, **without** a decimal point.

- **Floats** (floating-point numbers) are numbers, both positive and negative, **with** a decimal point.

- **Booleans** are either `True` or `False` — like a yes/no answer. The name "Boolean" comes from the mathematician George Boole.

Integers, floats, and Booleans are simple types — each variable holds a single value. Strings, on the other hand, are sequences of characters, and we'll explore them in depth in [Chapter 5](chapter-05.md).

## Type Conversion

Sometimes you need to change a value from one type to another. Python gives you built-in functions for this:

```python
# String to integer
age_text = "15"
age_number = int(age_text)
print(age_number + 1)

# String to float
pi_text = "3.14"
pi_number = float(pi_text)
print(pi_number)

# Number to string
score = 100
score_text = str(score)
print("Your score is " + score_text)

# Float to integer (cuts off the decimal — does NOT round)
x = int(3.9)
print(x)
```

**Output:**
```
16
3.14
Your score is 100
3
```

Type conversion is especially useful with `input()`, since `input()` always returns a string:

```python
age = int(input("How old are you? "))
print("Next year you'll be", age + 1)
```

**Output:**
```
How old are you? 10
Next year you'll be 11
```

You can check what type a value is using `type()`:

```python
x = 5
print(type(x))
y = "hello"
print(type(y))
```

**Output:**
```
<class 'int'>
<class 'str'>
```

## Operators

Python supports a series of math operators:

```python
x = 9
y = 2

sm = x + y          # Sum: 11
diff = x - y        # Difference: 7
prod = x * y        # Product: 18
quo = x / y         # Quotient: 4.5
intquo = x // y     # Floored Quotient: 4
mod = x % y         # Modulus (Remainder): 1
pwr = x ** y        # Power (x to the y): 81

print(sm, diff, prod, quo, intquo, mod, pwr)
```

**Output:**
```
11 7 18 4.5 4 1 81
```

There are two kinds of division: `/` gives the full decimal answer (a float), while `//` gives the answer rounded **down** to a whole number (called **floor division**).

The **modulus** operator `%` gives you the **remainder** after division. For example, `9 % 2` is `1` because 9 divided by 2 is 4 with a remainder of 1. This is very handy for checking whether a number is even or odd: if `n % 2 == 0`, the number is even.

### Assignment Operator Shortcuts

If you want to update a variable using its current value, you can use shortcut operators. For example, instead of writing `x = x + y`, you can write `x += y`:

| Long Form | Short Form |
|-----------|------------|
| `x = x + y` | `x += y` |
| `x = x - y` | `x -= y` |
| `x = x * y` | `x *= y` |
| `x = x / y` | `x /= y` |
| `x = x // y` | `x //= y` |
| `x = x % y` | `x %= y` |
| `x = x ** y` | `x **= y` |

---

## Navigation

⬅️ **[Previous: Chapter 1 - Hello World](chapter-01.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 3 - If/Elif/Else Statements](chapter-03.md)**
