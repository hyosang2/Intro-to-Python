---
layout: default
title: Chapter 3 - If/Elif/Else Statements
---

# Chapter 3: If/Elif/Else Statements

Most decision-making in Python uses **if-statements**. It's like the "if-then-else" block in Scratch. To create an if-statement, follow these steps:

1. Write the **`if`** keyword
2. Define the **condition** to check
3. Write the **body** — the code that runs if the condition is true

The body is defined by **indenting** a block of lines (usually 4 spaces). These lines only run if the condition is true. A condition is true when it simplifies to the Boolean value `True`.

By adding the optional **`else`** keyword, you can define a second body that runs only if the condition is false.

```python
x = 3
y = 7
if x > y:  # This simplifies to False
    print("x is greater than y.")
else:  # In other words, x <= y.
    print("x is less than or equal to y.")
```

**Output:**
```
x is less than or equal to y.
```

This prints `x is less than or equal to y.` because the condition `x > y` evaluates to `False`.

## Elif Statements

The optional **`elif`** keyword (short for "else if") lets you check a second condition when the first one is not satisfied:

```python
x = 7
y = 3
if x > y:
    print("x is greater than y.")
elif x < y:
    print("x is less than y.")
else:  # In other words, x == y.
    print("x is equal to y.")
```

**Output:**
```
x is greater than y.
```

Once a condition is met, Python will **skip all the remaining `elif` and `else` branches** below it. You can chain as many `elif` branches as you need.

## Comparison Operators

These are the symbols used to compare values in Python:

| Python Syntax | Meaning |
|--------------|---------|
| `x == y` | $x = y$ (equal to) |
| `x != y` | $x \neq y$ (not equal to) |
| `x > y` | $x > y$ (greater than) |
| `x < y` | $x < y$ (less than) |
| `x >= y` | $x \geq y$ (greater than or equal to) |
| `x <= y` | $x \leq y$ (less than or equal to) |

Note that the double equal sign (`==`) **compares** two values to check if they're equal, while the single equal sign (`=`) **assigns** a value to a variable. Mixing these up is a very common beginner mistake!

## Logical Operators: `and`, `or`, `not`

You can combine conditions using `and`, `or`, and `not` to create **compound conditions**:

- `a and b` is true if **both** `a` and `b` are true.
- `a or b` is true if **at least one** of `a` or `b` is true.
- `not a` is true if `a` is false (it flips the result).

```python
age = 20
has_drivers_license = True
if age >= 18 and has_drivers_license:
    print("You can drive.")

is_student = True
is_employed = False
if is_student or is_employed:
    print("You can get a discount.")

is_hungry = False
if not is_hungry:
    print("You are full.")
```

**Output:**
```
You can drive.
You can get a discount.
You are full.
```

When mixing operators, `not` is evaluated first, then `and`, then `or`. Parentheses can be used to change the order, just like in math. To practice this, try building **truth tables** for compound conditions.

## Nested If-Statements

Sometimes you need to check a second condition only after the first one passes. You can put an if-statement *inside* another if-statement — this is called **nesting**.

```python
age = 20
has_drivers_license = False
has_training_permit = True
if age >= 18:
    if has_drivers_license:
        print("You can drive.")
    elif has_training_permit:
        print("You can drive under supervision.")
    else:
        print("You cannot drive.")
else:
    print("You cannot drive.")
```

**Output:**
```
You can drive under supervision.
```

You can nest as many layers of if-statements as you need, but try to keep it readable. Often, compound conditions with `and`/`or` can replace deeply nested code.

---

## Navigation

⬅️ **[Previous: Chapter 2 - Variables and Data Types](chapter-02.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 4 - Loops](chapter-04.md)**
