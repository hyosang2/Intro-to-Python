---
layout: default
title: Chapter 2 - Variables and Data Types
---

# Chapter 2: Variables and Data Types

A **variable** in Python is a data storage and tracking asset.

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

In the above code, the first two lines **assigned** values on the right-hand-side of `=` to the respective variable on the left-hand-side. Now, `x` and `y` are variables, each representing a specific value.

By common practice, variables are named in lower-case alphabets and numbers spaced with underscores (`"_"`). **Names that use non-alphanumeric characters (other than underscores) or start with a number are not allowed.**

## Data Types

Python supports various data types such as **integers**, **strings**, **floats**, and **Booleans**:

```python
location = "Pasadena, CA"   # String
x = 7                       # Integer
y = 3.14                    # Float
is_daytime = True           # Boolean
```

Integers, floats, and Boolean types are classified as **primitive data types**, which implies that a variable holds a single piece of data. In contrast, strings are not primitive because they are sequences of characters, implying that they comprise multiple data units.

### Understanding Data Types

- **Strings** are ordered data sets made up of a group of characters, such as letters, numbers, and punctuation marks. These data are represented by enclosing the words or phrases within a pair of single or double quotation marks.

- **Integers** are numbers, both positive and negative, **without** a decimal point.

- **Floats** (floating numbers) are numbers, both positive and negative, **with** a decimal point.

- **Boolean** values can be either `True` or `False`.

If you're familiar with other common languages like Java or C++, you'll notice that in Python, the data type isn't explicitly specified when defining a variable. If you're familiar with languages like C# or JavaScript, you also won't find variable markers like `local` or `let`. However, as a compensation, it's crucial to always *initialize* a variable when defining it.

## Operators

Python supports a series of operators, including addition, subtraction, multiplication, division, modulus (remainder), and power.

```python
x = 9            # 9 is assigned to x.
y = 2            # 2 is assigned to y.

sm = x + y          # Sum
diff = x - y        # Difference
prod = x * y        # Product
quo = x / y         # Quotient
intquo = x // y     # Floored Quotient
mod = x % y         # Modulus (Remainder)
pwr = x ** y        # Power (x^y)

print(sm, diff, prod, quo, intquo, mod, pwr)
```

**Output:**
```
11 7 18 4.5 4 1 81
```

There are two modes of division: `/` gives a quotient in decimal (float) form, whereas `//` gives a quotient in integer, **floored**, or rounded down, from the decimal.

### Assignment Operator Shortcuts

If any of the *binary* operations assigns the output back to the same variable, such as `x = x + y`, they can be shortened into the following:

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