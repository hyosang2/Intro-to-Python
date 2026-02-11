---
layout: default
title: Chapter 6 - Lists
---

# Chapter 6: Lists

A **list** is a collection of items **in a specific order**. Like Scratch lists, you can add, remove, and access items by position. Each item has an **index** (position number) starting at 0, just like strings.

```python
my_list = [1, 2, 3]

print(my_list[0])   # First item
print(my_list[1])   # Second item
print(my_list[-1])  # Last item
print(my_list[-2])  # Second to last
```

**Output:**
```
1
2
3
2
```

A list can contain items of different types, including other lists:

```python
mixed = [1, 2.4, "Coding", True, [2, 5]]
```

## Getting and Setting Items

You can read an item (get) or change it (set) using its index:

```python
my_list = [10, 20, 30]

# Get
print(my_list[0])  # 10

# Set
my_list[1] = 99
print(my_list)     # [10, 99, 30]
```

This is a key difference from strings: lists are **mutable**, meaning you can change their contents. Strings are **immutable** — you can't change a single character within a string.

## Slicing and Sublists

Slicing works the same way as with strings — you can grab a portion of a list (called a **sublist**) using `[start:stop:step]`:

```python
my_list = ["a", "b", "c", "d", "e"]
print(my_list[1:4])       # ['b', 'c', 'd']
print(my_list[:3])        # ['a', 'b', 'c']
print(my_list[2:])        # ['c', 'd', 'e']
print(my_list[::2])       # ['a', 'c', 'e']
print(my_list[::-1])      # ['e', 'd', 'c', 'b', 'a']
print(my_list[4:1:-1])    # ['e', 'd', 'c']
```

## List Traversal

Since lists are iterable (you can loop through them), you can use a for-loop to visit each item:

```python
my_list = [1, 2, 3]
for item in my_list:
    print(item)
```

**Output:**
```
1
2
3
```

If you also need each item's index, use `enumerate()`:

```python
colors = ["red", "green", "blue"]
for i, color in enumerate(colors):
    print(f"Index {i}: {color}")
```

**Output:**
```
Index 0: red
Index 1: green
Index 2: blue
```

## 2D Lists

Sometimes a flat list isn't enough — for example, when representing a grid or table. A **2D list** is a list that contains other lists as its items:

```python
grid = [["a", "b", "c"],
        ["d", "e", "f"],
        ["g", "h", "i"]]

print(grid[0][0])    # "a" (row 0, column 0)
print(grid[1][2])    # "f" (row 1, column 2)
```

To loop through a 2D list, use **nested for-loops** — one for the rows, one for the items in each row:

```python
for i, row in enumerate(grid):
    for j, item in enumerate(row):
        print(f"({i},{j}) = {item}")
```

**Output:**
```
(0,0) = a
(0,1) = b
(0,2) = c
(1,0) = d
(1,1) = e
(1,2) = f
(2,0) = g
(2,1) = h
(2,2) = i
```

You can build lists with three or more dimensions by adding more nested lists, but 2D is the most common.

## List Built-in Functions

Here are the most commonly used functions and methods for lists:

### Length

**`len(list)`** returns the number of items in a list.

```python
print(len([10, 20, 30]))  # 3
print(len([]))             # 0
```

### Adding Items

- **`.append(item)`** adds an item at the **end** of the list.
- **`.insert(index, item)`** adds an item at a specific position, pushing the rest forward.

```python
my_list = ["a", "b", "d"]
my_list.append("e")
print(my_list)            # ['a', 'b', 'd', 'e']

my_list.insert(2, "c")
print(my_list)            # ['a', 'b', 'c', 'd', 'e']
```

### Removing Items

- **`.pop(index)`** removes and returns the item at the given index. If no index is given, it removes the **last** item.
- **`.remove(value)`** removes the **first** item that matches the given value.

```python
my_list = ["a", "b", "c", "d"]

my_list.pop(0)
print(my_list)      # ['b', 'c', 'd']

my_list.pop()
print(my_list)      # ['b', 'c']

animals = ["cat", "dog", "cat", "bird"]
animals.remove("cat")
print(animals)      # ['dog', 'cat', 'bird'] — only the first "cat" is removed
```

### Searching

- **`value in list`** checks whether the list contains at least one item with that value.
- **`.index(value)`** returns the index of the **first** occurrence of the value.
- **`.count(value)`** counts how many times the value appears in the list.

```python
my_list = ["a", "b", "c", "b", "d"]

print("b" in my_list)        # True
print("z" in my_list)        # False
print(my_list.index("b"))    # 1 (the first "b")
print(my_list.count("b"))    # 2
```

### Sorting and Reversing

- **`.sort()`** sorts the list **in place** (changes the original list).
- **`.reverse()`** reverses the list **in place**.
- **`sorted(list)`** returns a **new** sorted list, leaving the original unchanged.

```python
numbers = [3, 1, 4, 1, 5, 9]

print(sorted(numbers))  # [1, 1, 3, 4, 5, 9] — new list
print(numbers)           # [3, 1, 4, 1, 5, 9] — original unchanged

numbers.sort()
print(numbers)           # [1, 1, 3, 4, 5, 9] — original is now sorted

numbers.reverse()
print(numbers)           # [9, 5, 4, 3, 1, 1]
```

There are many more list functions available — it's always worth searching for "Python list methods" when you need something specific.

Try it yourself! Write a program that takes a list of numbers and prints only the ones that are greater than the average.

---

## Navigation

⬅️ **[Previous: Chapter 5 - Strings](chapter-05.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 7 - Tuples, Dictionaries, and Sets](chapter-07.md)**
