---
layout: default
title: Chapter 4 - Loops
---

# Chapter 4: Loops

Sometimes you want certain code to run multiple times. Maybe each cycle is slightly different, but you notice a repeating pattern. That's when you use **loops**.

## While-Loops

Recall if-statements: the body runs only if the condition is true. If you replace the `if` keyword with `while`, the body will **repeat** as long as the condition stays true. It stops once the condition becomes false.

```python
i = 0
while i < 5:
    print(i)
    i += 1
```

**Output:**
```
0
1
2
3
4
```

This code prints the value of `i`, starting at 0, adds 1 to it, and repeats until `i` reaches 5 (at which point `i < 5` is false, so the loop stops). It's similar to the "repeat until" block in Scratch, except Scratch's version stops when the condition becomes true, while Python's while-loop repeats *while* the condition is true.

**Think about it:** How can you make a loop that repeats forever, like the "forever" block in Scratch? Hint: what condition is *always* true?

## For-Loops

Unlike while-loops that check a condition each time, for-loops **go through** a sequence of items and process one item at a time. Data that you can loop through is called **iterable** — meaning "something you can go through one item at a time." Examples include a range of numbers, the characters of a string, and lists.

```python
for i in range(5):
    print(i)

for letter in "Python":
    print(letter)
```

**Output:**
```
0
1
2
3
4
P
y
t
h
o
n
```

The first for-loop behaves the same as the while-loop example above. `range(5)` gives you the numbers 0 through 4, and `i` takes on each number in order. The second for-loop goes through each character in the string `"Python"`, one at a time.

### The `range()` Function

`range()` gives you a sequence of numbers. It can be called in three ways:

```python
range(stop)                # Numbers from 0 up to (but not including) stop
range(start, stop)         # Numbers from start up to (but not including) stop
range(start, stop, step)   # Same, but counting by step instead of 1
```

All values must be integers. The `stop` value is always **excluded** from the range.

```python
range(4)          # 0, 1, 2, 3
range(2, 10, 2)   # 2, 4, 6, 8
range(0, 7, 2)    # 0, 2, 4, 6
range(6, -1, -2)  # 6, 4, 2, 0
```

To count *backwards*, use a negative `step` and make `start` larger than `stop`.

### The `enumerate()` Function

Sometimes you need both the **index** (position number) and the **value** of each item while looping. The `enumerate()` function gives you both:

```python
fruits = ["apple", "banana", "cherry"]
for i, fruit in enumerate(fruits):
    print(i, fruit)
```

**Output:**
```
0 apple
1 banana
2 cherry
```

Here, `i` gets the index (0, 1, 2) and `fruit` gets the value at that index. This works with any iterable — strings, lists, and more.

## Nested Loops

Just like nested if-statements, you can put a loop *inside* another loop. This is useful when you need to repeat a pattern within a pattern, such as going through the rows and columns of a grid.

```python
for i in range(3):
    j = 0
    while j < 5:
        print(i, j)
        j += 1
```

**Output:**
```
0 0
0 1
0 2
0 3
0 4
1 0
1 1
...
```

The outer loop runs 3 times, and for each of those, the inner loop runs 5 times — giving you a total of 15 `print` statements. A loop moves to the next cycle only after finishing all the code in its body, including any inner loops.

## `break` and `continue`

The keywords `break` and `continue` give you extra control inside loops:

- **`break`** exits the loop entirely.
- **`continue`** skips the rest of the current cycle and jumps to the next one.

```python
for i in range(10):
    if i == 5:
        break
    print(i)

for i in range(10):
    if i % 2 == 1:
        continue
    print(i)
```

**Output:**
```
0
1
2
3
4
0
2
4
6
8
```

The first loop prints `i` up to 4 because it exits when `i` reaches 5. The second loop skips odd numbers (when `i % 2 == 1`) and only prints the even ones.

## The Accumulator Pattern

One of the most important patterns in programming is **building up a result inside a loop**. You start with an empty result (like `0` for a sum, `""` for a string, or `[]` for a list), then add to it on each cycle. This is called the **accumulator pattern**.

### Accumulating a Sum

```python
total = 0
for num in [10, 20, 30, 40]:
    total += num
print(total)
```

**Output:**
```
100
```

### Building a String

```python
result = ""
for letter in "Hello":
    result += letter + letter
print(result)
```

**Output:**
```
HHeelllloo
```

### Building a List

```python
evens = []
for num in [1, 2, 3, 4, 5, 6]:
    if num % 2 == 0:
        evens.append(num)
print(evens)
```

**Output:**
```
[2, 4, 6]
```

This pattern shows up everywhere in programming — in CodingBat problems, real-world projects, and beyond. Whenever you need to process a sequence and collect results, think "accumulator pattern."

Try it yourself! Write a loop that adds up all the numbers from 1 to 100.

---

## Navigation

⬅️ **[Previous: Chapter 3 - If/Elif/Else Statements](chapter-03.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 5 - Strings](chapter-05.md)**
