---
layout: default
title: Chapter 4 - Loops
---

# Chapter 4: Loops

Sometimes we want certain codes to run multiple times. Perhaps each cycle differs a bit, but you notice a pattern inside of it. In this case, we use **loops**. There are two ways to use loops.

## While-Loops

Recall if-statements. The body is run only if the condition is true. By replacing the `if` syntax with `while`, the body will *repeat* while the condition is **true**. In other words, it will *stop repeating* once the condition becomes **false**.

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

Above code will print the value of `i`, starting with 0, increment the value by 1, and repeat, until `i` becomes 5 (exclusive). It is similar to the "repeat until" block in Scratch, except while-loops behave the opposite with the condition.

Using the while-loop, how can we simulate the "forever" block in Scratch, where the body repeats infinitely? (Hint: think of an if-statement that *always* passes.)

## For-Loops

Unlike while-loops that repeatedly check a condition to continue executing, for-loops **traverse through** iterable data and retrieve an item from the data in each iteration. Data is considered **iterable** if a loop can be used to iterate through its contents. Examples include a range of integers via `range()`, the letters of a string, or lists.

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

The first for-loop behaves the same as the previous code. `range(5)` gives you a range of integers from 0 to 4, inclusive. While there are more use cases of `range()` (see next part), in here, `i` is assigned with each number of the range in order per iteration. Overall, this for-loop repeats 5 times.

### The `range()` Function

`range()` is a function that can give you not just the range of numbers starting at 0.

```python
range(start=0, end, step=1)
```

where all parameters are integers, and `start` and `step` are defaulted at `0` and `1`, respectively. It returns a range of numbers starting at `start` (inclusive) and stops at `end` (exclusive), where the distance between two consecutive numbers in the range is `step`. This is why `range(5)` gives you the range from 0 to 4, spaced by 1.

To *reverse* the order of a range of numbers, simply make the `step` negative and swap the values of `start` and `end`. However, be sure to consider whether the range is inclusive or exclusive.

```python
range(4)          # 0, 1, 2, 3
range(2, 10, 2)   # 2, 4, 6, 8
range(0, 7, 2)    # 0, 2, 4, 6
range(6, -1, -2)  # 6, 4, 2, 0
```

## Nested Loops

Like nested if-statements, loops can be nested by each other as well. This is useful for cycles where each sequence requires running a separate cycle, such as 2D lists.

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

Remember that a loop moves to the next cycle after reaching the end of its body in the current cycle.

## `break` and `continue`

The two syntax `break` and `continue` are used to exit a loop or the current cycle of the loop, respectively. For example:

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

The first for-loop will print `i` up to 4 because the loop exits when `i` reaches 5. The second for-loop will only print even numbers because the cycle is skipped if `i` is an odd number.

---

## Navigation

⬅️ **[Previous: Chapter 3 - If/Elif/Else Statements](chapter-03)**

⬅️ **[Back to Table of Contents](table-of-contents)**

➡️ **[Next: Chapter 5 - Collections](chapter-05)**