---
layout: default
title: Chapter 3 - If-Else Statements
---

# Chapter 3: If-Else Statements

Most logics in Python consist of **if-statements**. To create an if-statement, we do the following steps:

1. Insert an **`if`** keyword
2. Define the **condition** to satisfy
3. Insert the **body**

The bodies are defined by **indenting** a block of lines. These lines are executed only if the condition defined in the if-statement is *true*. A condition being true means that the condition can be *simplified into the value `True`* (recall the Boolean values).

By using the optional **`else`** keyword, we can define another body to be executed only if the condition is *false* (the condition *simplifies into the value `False`*).

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

If above code is run, it will print `x is less than or equal to y.` because the condition `x > y` evaluates to false.

## Elif Statements

By using the optional **`elif`** keyword (`elif` stands for "else if"), we can define a second condition to check if the preceding condition is not satisfied.

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

Note that if the previous condition is met, the compiler will **ignore the conditions and bodies in the subsequent `elif`- and `else`-statements**.

## Inequality Operators

These are the syntax to represent inequalities in Python:

| Python Syntax | Mathematical Meaning |
|--------------|---------------------|
| `x == y` | x = y |
| `x > y` | x > y |
| `x < y` | x < y |
| `x >= y` | x ≥ y |
| `x <= y` | x ≤ y |
| `x != y` | x ≠ y |

Note that the double equal signs (`==`) is used to express the *condition of two variables with equal values*, while the single equal sign (`=`) *assigns a value into a variable*.

## Logical Operators: `and`, `or`, `not`

We can create *compound conditions* with a mix of `and`, `or`, and `not` syntax.

- `a and b` outputs true if **both** conditions `a` and `b` are true.
- `a or b` outputs true if **at least one** condition of `a` or `b` is true.
- `not a` outputs true if `a` is **not** true.

```python
age = 20
has_drivers_license = True
if age >= 18 and has_drivers_license:
    print("You can drive.")

is_student = True
is_employed = False
if is_student or is_employed:
    print("You can get discount.")

is_hungry = False
if not is_hungry:
    print("You are full.")
```

**Output:**
```
You can drive.
You can get discount.
You are full.
```

The **order of operations matter** in compound condition. That is, `not` is operated first, then `and` and `or` in order. Parentheses can be used to change the order. To familiarize with this, consider practicing to build **truth tables** with given compound conditions.

## Nested If-Statements

Suppose condition `a` is true, and one wants to build a consequential action that depends on whether condition `b` is true or false. That's when the nested if-statement comes in. A series of if-statements can be wrapped as a followup action of an outer if-statement.

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

Multiple layers of if-statements are allowed.

---

## Navigation

⬅️ **[Previous: Chapter 2 - Variables and Data Types](chapter-02.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 4 - Loops](chapter-04.md)**