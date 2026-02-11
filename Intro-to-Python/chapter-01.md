---
layout: default
title: Chapter 1 - Hello World
---

# Chapter 1: Hello World

Welcome to Python! Python is one of the most popular programming languages in the world, and it's a great first language to learn. In this guide, you'll learn everything you need to start writing your own programs.

## Getting Started

To write and run Python code, you can use a free online editor like [replit.com](https://replit.com/) or [python.org/shell](https://www.python.org/shell/). Just type your code and hit the Run button. If Python is installed on your computer, you can also save your code in a `.py` file and run it from the terminal with `python my_file.py`.

## Print Statements

The first step in programming is to display something on the screen. We do this with a **print statement**:

```python
print("Hello World!")
```

**Output:**
```
Hello World!
```

Think of `print()` as a way to make the computer talk to you. Whatever you put inside the parentheses and quotation marks will appear on the screen. Print statements are useful for showing results and figuring out what your code is doing.

You can print multiple things by separating them with commas:

```python
print("My name is", "Alice")
print("I am", 10, "years old")
```

**Output:**
```
My name is Alice
I am 10 years old
```

## Comments

Throughout this guide, you'll see text that follows a `#` symbol. These are **comments**. Comments don't do anything when the code runs — they're notes that describe what the code does.

```python
print("Hello World!")
# I don't do anything. I'm just a note!
```

**Output:**
```
Hello World!
```

Comments are helpful for:

- Explaining what your code does
- Adding notes for future reference
- Temporarily disabling a line of code without deleting it
- Making your code easier to read for others

## Input

What if you want the user to type something? The **`input()`** function lets you ask a question and save the answer. It's like the "ask and wait" block in Scratch.

```python
name = input("What is your name? ")
print("Hello, " + name + "!")
```

**Output:**
```
What is your name? Gary
Hello, Gary!
```

In the example above, `"Gary"` is typed by the user while the program is running. The `input()` function always gives you text (a string), even if the user types a number. We'll learn how to convert between types in the next chapter.

Try it yourself! Write a program that asks for the user's name and favorite color, then prints a sentence using both.

---

## Navigation

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 2 - Variables and Data Types](chapter-02.md)**
