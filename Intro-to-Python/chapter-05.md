---
layout: default
title: Chapter 5 - Strings
---

# Chapter 5: Strings

Recall from [Chapter 2](chapter-02.md) that strings are text enclosed in quotation marks. While they look like simple values, strings are actually **collections of characters**. Each character sits at a specific position called an **index**, starting at 0. This makes strings one of Python's most feature-rich data types.

For example, the string `"Hello"` contains five characters: `'H'` at index 0, `'e'` at index 1, `'l'` at index 2, `'l'` at index 3, and `'o'` at index 4.

## String Concatenation

Strings can be **concatenated** (joined together) using the `+` operator. If you need to include a number in a string, convert it to a string first using `str()`.

```python
greeting = "Hello " + "world!"
print(greeting)

greeting2 = greeting + " How are you?"
print(greeting2)

greeting2 += " I'm great!"
print(greeting2)

age = 15
message = "I am " + str(age) + " years old!"
print(message)
```

**Output:**
```
Hello world!
Hello world! How are you?
Hello world! How are you? I'm great!
I am 15 years old!
```

### F-Strings

Python 3.6 introduced **f-strings**, a much easier way to insert variables into strings. Put an `f` before the opening quotation mark, then use curly braces `{}` around any variable or expression:

```python
name = "Alice"
age = 15
print(f"My name is {name} and I am {age} years old!")
print(f"Next year I'll be {age + 1}.")
```

**Output:**
```
My name is Alice and I am 15 years old!
Next year I'll be 16.
```

F-strings don't require `str()` conversion — you can put any expression inside the curly braces.

## Indexing

You can access a single character from a string using its **index** in square brackets. Remember, indexing starts at 0!

```python
my_string = "Python"
print(my_string[0])   # First character
print(my_string[3])   # Fourth character
print(my_string[-1])  # Last character
print(my_string[-2])  # Second to last character
```

**Output:**
```
P
h
n
o
```

**Negative indices** count from the end: `-1` is the last character, `-2` is the second to last, and so on. This is really handy when you need to grab characters from the end without knowing the string's length.

## Slicing and Substrings

**Slicing** lets you grab a portion of a string. The result is called a **substring** — a string made up of some characters from another string. The general syntax is:

```python
string[start:stop:step]
```

- `start`: the index to begin at (inclusive, defaults to 0)
- `stop`: the index to stop at (exclusive, defaults to end of string)
- `step`: how many characters to skip (defaults to 1)

```python
my_string = "Hello world!"
print(my_string[0:5])     # Characters from index 0 to 4
print(my_string[6:11])    # Characters from index 6 to 10
print(my_string[:5])      # From the start to index 4
print(my_string[6:])      # From index 6 to the end
print(my_string[::2])     # Every other character
print(my_string[::-1])    # The entire string, reversed!
```

**Output:**
```
Hello
world
Hello
world!
Hlowrd
!dlrow olleH
```

The trick `[::-1]` reverses any string — it's a useful pattern to remember.

## String Traversal

You can loop through a string character by character:

```python
for letter in "Python":
    print(letter)
```

**Output:**
```
P
y
t
h
o
n
```

If you also need the index, use `enumerate()`:

```python
for i, letter in enumerate("Cat"):
    print(f"Index {i}: {letter}")
```

**Output:**
```
Index 0: C
Index 1: a
Index 2: t
```

## String Built-in Functions

Here are the most commonly used string functions and methods:

### Length

**`len(string)`** returns the number of characters in a string.

```python
print(len("Hello"))    # 5
print(len(""))         # 0
print(len("Hi there")) # 8 (the space counts!)
```

### Changing Case

```python
my_string = "Hello World"
print(my_string.upper())  # "HELLO WORLD"
print(my_string.lower())  # "hello world"
```

### Checking Content

- **`substring in string`** checks if a string contains another string.
- **`.startswith(s)`** checks if the string starts with `s`.
- **`.endswith(s)`** checks if the string ends with `s`.
- **`.isdigit()`** checks if every character is a digit.

```python
my_string = "Hello World"
print("World" in my_string)          # True
print("world" in my_string)          # False (case-sensitive!)
print(my_string.startswith("Hello")) # True
print(my_string.endswith("World"))   # True
print("12345".isdigit())             # True
print("12.5".isdigit())              # False
```

### Finding and Counting

- **`.find(sub)`** returns the index of the first occurrence of `sub`, or `-1` if not found.
- **`.count(sub)`** counts how many times `sub` appears.

```python
sentence = "the cat sat on the mat"
print(sentence.find("cat"))    # 4
print(sentence.find("dog"))    # -1
print(sentence.count("the"))   # 2
print(sentence.count("at"))    # 3
```

### Replacing

**`.replace(old, new)`** replaces all occurrences of `old` with `new` and returns a new string.

```python
sentence = "I like cats and cats like me"
new_sentence = sentence.replace("cats", "dogs")
print(new_sentence)  # "I like dogs and dogs like me"
```

### Splitting and Joining

- **`.split(sep)`** splits a string into a list of parts. If no separator is given, it splits on spaces.
- **`sep.join(list)`** joins a list of strings into one string, with `sep` between each item.

```python
sentence = "apple,banana,cherry"
fruits = sentence.split(",")
print(fruits)  # ['apple', 'banana', 'cherry']

words = ["Hello", "World"]
result = " ".join(words)
print(result)  # "Hello World"
```

### Stripping Whitespace

**`.strip()`** removes extra spaces (and newlines) from the beginning and end of a string.

```python
messy = "   Hello World   "
print(messy.strip())  # "Hello World"
```

There are many more string methods — whenever you need to do something specific with strings, try searching "Python string methods" online.

Try it yourself! Write a program that takes a sentence and counts how many words it has. (Hint: use `.split()`.)

---

## Navigation

⬅️ **[Previous: Chapter 4 - Loops](chapter-04.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 6 - Lists](chapter-06.md)**
