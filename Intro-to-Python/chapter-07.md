---
layout: default
title: Chapter 7 - Tuples, Dictionaries, and Sets
---

# Chapter 7: Tuples, Dictionaries, and Sets

Beyond strings and lists, Python has three more collection types that are useful in different situations.

## Tuples

A **tuple** is similar to a list, but it's **immutable** — once you create it, you can't change its items or length. Tuples use parentheses `()` instead of square brackets `[]`.

```python
my_tuple = (0, 0)
print(my_tuple)
print(my_tuple[0])  # Indexing works the same as lists

my_tuple = (0, 1)   # You can reassign the whole tuple...
print(my_tuple)

my_tuple[0] = 1     # ...but you can't change individual items!
```

**Output:**
```
(0, 0)
0
(0, 1)
TypeError: 'tuple' object does not support item assignment
```

When should you use a tuple instead of a list? Tuples are great for data that shouldn't change, like a pair of coordinates `(x, y)` or a date `(year, month, day)`. They also use slightly less memory than lists.

You can loop through tuples and use indexing/slicing just like lists:

```python
colors = ("red", "green", "blue")
for color in colors:
    print(color)

print(colors[1:])  # ('green', 'blue')
```

## Dictionaries

A **dictionary** stores data as **key-value pairs**. Instead of accessing items by their position number (index), you access them by a unique **key**. Think of it like a real dictionary: you look up a word (the key) to find its definition (the value).

```python
scores = {"Andrew": 8, "Brian": 5, "Charlie": 10}

# Access a value using its key
print(scores["Brian"])  # 5

# Change a value
scores["Brian"] = 9
print(scores["Brian"])  # 9
```

**Output:**
```
5
9
```

Dictionaries use curly braces `{}` with key-value pairs separated by colons `:`.

Since **Python 3.7+**, dictionaries maintain the order in which items were added. However, unlike lists, you access items by key rather than by integer index.

### Keys and Values

The keys of a dictionary must be **immutable** types (strings, numbers, tuples) and must be **unique**. Values can be any type.

```python
my_dict = {"David": 9,
           8: ["Hello", "Hi"],
           (1, 2): 2.4}

print(my_dict[(1, 2)])  # 2.4
```

### Looping Through Dictionaries

You can loop through a dictionary's keys, values, or both:

```python
scores = {"Andrew": 8, "Brian": 5, "Charlie": 10}

# Loop through keys
for name in scores:
    print(name)

# Loop through values
for score in scores.values():
    print(score)

# Loop through key-value pairs
for name, score in scores.items():
    print(f"{name}: {score}")
```

**Output:**
```
Andrew
Brian
Charlie
8
5
10
Andrew: 8
Brian: 5
Charlie: 10
```

Note: `keys()`, `values()`, and `items()` return special view objects, not lists. If you need an actual list, wrap them with `list()`:

```python
key_list = list(scores.keys())
print(key_list)  # ['Andrew', 'Brian', 'Charlie']
```

### Dictionary Built-in Functions

**Adding and removing items:**

```python
scores = {"Andrew": 8, "Brian": 5, "Charlie": 10}

# Add a new key-value pair
scores["Daniel"] = 12
print(scores)
# {'Andrew': 8, 'Brian': 5, 'Charlie': 10, 'Daniel': 12}

# Remove a key-value pair and get the value back
removed = scores.pop("Brian")
print(removed)  # 5
print(scores)   # {'Andrew': 8, 'Charlie': 10, 'Daniel': 12}
```

**Checking if a key exists:**

```python
print("Charlie" in scores)  # True
print("Brian" in scores)    # False
```

Note that `in` checks for **keys**, not values.

**Safe access with `.get()`:**

Sometimes you're not sure if a key exists. Using `[key]` would cause an error, but `.get(key, default)` returns the value if the key exists, or a default value if it doesn't:

```python
scores = {"Andrew": 8, "Charlie": 10}

print(scores.get("Andrew"))      # 8
print(scores.get("Daniel"))      # None
print(scores.get("Daniel", 0))   # 0 (custom default)
```

**Length:** `len(my_dict)` returns the number of key-value pairs.

## Sets

A **set** is a collection where every item is **unique** — no duplicates allowed. If you add an item that's already there, nothing happens. Sets also use curly braces `{}`, but without the colon `:` that dictionaries use.

```python
my_set = {1, 2, 3, 4, 1}  # The duplicate 1 is removed
print(my_set)              # {1, 2, 3, 4}

empty_set = set()  # Use set(), not {} (which creates an empty dictionary)
print(type(empty_set))     # <class 'set'>
```

Sets are **unordered**, so you can't access items by index. But you can loop through them and check if a value exists:

```python
my_set = {1, 2, 3, 4}

for num in my_set:
    print(num)

print(2 in my_set)  # True
print(5 in my_set)  # False
```

### Set Built-in Functions

- **`.add(value)`** adds a value to the set.
- **`.remove(value)`** removes a value (throws an error if not found).
- **`.discard(value)`** removes a value (does nothing if not found — safer than `.remove()`).

```python
my_set = {1, 2, 3, 4}

my_set.add(5)
print(my_set)      # {1, 2, 3, 4, 5}

my_set.add(3)      # Already exists — no change, no error
print(my_set)      # {1, 2, 3, 4, 5}

my_set.remove(3)
print(my_set)      # {1, 2, 4, 5}
```

Sets also support mathematical operations like union, intersection, and difference — search "Python set operations" to learn more!

---

## Navigation

⬅️ **[Previous: Chapter 6 - Lists](chapter-06.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 8 - Functions](chapter-08.md)**
