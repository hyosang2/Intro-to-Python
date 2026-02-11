---
layout: default
title: Chapter 5 - Turtle Graphics
---

# Chapter 5: Turtle Graphics

**Turtle** is a Python library that lets you draw pictures using simple commands. Think of it as a digital pen that follows your instructions to move around and draw lines, shapes, and colorful patterns. Turtle comes built-in with Python, so you don't need to install anything extra.

Turtle is a great bridge between the OOP concepts from Chapters 2–3 and practical programming — every turtle you create is an **object** with its own properties (position, color, direction) and methods (`forward()`, `right()`, `circle()`).

## Basic Turtle Commands

```python
import turtle

# Create a turtle object and a screen object
my_turtle = turtle.Turtle()
screen = turtle.Screen()

# Basic movement
my_turtle.forward(100)    # Move forward 100 steps
my_turtle.right(90)       # Turn right 90 degrees
my_turtle.forward(50)     # Move forward 50 steps
my_turtle.left(45)        # Turn left 45 degrees
my_turtle.backward(75)    # Move backward 75 steps

# Keep the window open until clicked
screen.exitonclick()
```

When you run this, a window opens and you see lines appear as the turtle moves!

## Drawing Shapes

Using loops makes drawing shapes easy:

```python
import turtle

artist = turtle.Turtle()
screen = turtle.Screen()

# Draw a square (4 sides, 90-degree turns)
for i in range(4):
    artist.forward(100)
    artist.right(90)

# Move without drawing
artist.penup()
artist.goto(150, 0)
artist.pendown()

# Draw a triangle (3 sides, 120-degree turns)
for i in range(3):
    artist.forward(80)
    artist.right(120)

screen.exitonclick()
```

The general pattern is: a regular polygon with `n` sides uses turns of `360 / n` degrees.

## Colors and Pen Control

```python
import turtle

painter = turtle.Turtle()
screen = turtle.Screen()
screen.bgcolor("lightblue")

painter.color("red")
painter.pensize(5)
painter.speed(3)        # 1 = slowest, 10 = fast, 0 = instant

# Draw a flower (6 overlapping circles)
for i in range(6):
    painter.circle(50)
    painter.right(60)

# Draw the stem
painter.color("green")
painter.pensize(8)
painter.right(90)
painter.forward(150)

screen.exitonclick()
```

### Understanding Colors

There are two ways to specify colors:

**Color names** — easy to use:
```python
painter.color("red")
painter.color("purple")
painter.color("lightblue")
```

**RGB tuples** — mix Red, Green, and Blue (0–255 each):
```python
screen = turtle.Screen()
screen.colormode(255)        # Enable 0–255 mode

painter.color((255, 0, 0))    # Pure red
painter.color((0, 255, 0))    # Pure green
painter.color((0, 0, 255))    # Pure blue
painter.color((255, 255, 0))  # Yellow (red + green)
painter.color((0, 0, 0))      # Black (no color)
painter.color((255, 255, 255)) # White (all colors)
```

RGB colors are important because Pygame (Chapter 6) uses the same system.

## Displaying Text

The `write()` method lets you put text on the screen:

```python
import turtle

writer = turtle.Turtle()
writer.hideturtle()      # Hide the turtle shape

writer.goto(0, 100)
writer.write("Hello!", align="center", font=("Arial", 24, "bold"))

writer.goto(0, 50)
writer.color("blue")
writer.write("Centered text", align="center", font=("Arial", 14, "normal"))
```

The `font` takes a tuple of `("FontName", size, "style")`, and `align` can be `"left"`, `"center"`, or `"right"`.

## Keyboard Input

Turtle can respond to key presses, making programs interactive:

```python
import turtle

my_turtle = turtle.Turtle()
screen = turtle.Screen()

def move_up():
    my_turtle.setheading(90)
    my_turtle.forward(20)

def move_down():
    my_turtle.setheading(270)
    my_turtle.forward(20)

# Connect keys to functions
screen.onkey(move_up, "Up")
screen.onkey(move_down, "Down")
screen.listen()   # Start listening for key presses

screen.exitonclick()
```

**Key rules:**
- Call `screen.listen()` to activate keyboard input
- Use lowercase for letter keys: `"a"`, `"b"`, `"c"`
- Arrow keys: `"Up"`, `"Down"`, `"Left"`, `"Right"`
- Special keys: `"space"`, `"Return"`, `"Delete"`

## Turtle and OOP

Here's where turtle connects to everything from Chapters 2–3. We can create custom classes that wrap turtle objects:

```python
import turtle

class DrawingTurtle:
    def __init__(self, name, color, size):
        self.name = name
        self.turtle = turtle.Turtle()
        self.turtle.color(color)
        self.turtle.pensize(size)
        self.turtle.speed(5)

    def draw_square(self, side_length):
        for i in range(4):
            self.turtle.forward(side_length)
            self.turtle.right(90)

    def draw_circle(self, radius):
        self.turtle.circle(radius)

    def move_to(self, x, y):
        self.turtle.penup()
        self.turtle.goto(x, y)
        self.turtle.pendown()

# Create turtle objects — each has its own color and pen size
artist1 = DrawingTurtle("Pablo", "blue", 3)
artist2 = DrawingTurtle("Penny", "purple", 5)

screen = turtle.Screen()

artist1.draw_square(80)
artist1.move_to(200, 100)
artist1.draw_circle(40)

artist2.move_to(-200, -100)
artist2.draw_square(60)

screen.exitonclick()
```

This demonstrates core OOP concepts in action: each `DrawingTurtle` is an **object** with its own state (name, color, size) and behaviors (draw_square, draw_circle). Different objects operate independently — **encapsulation** and **polymorphism** at work.

Try it yourself! Create a `ColorfulTurtle` class with a method `draw_star(size)` that draws a five-pointed star. Make three turtles with different colors and have each one draw a star at a different position.

---

## Navigation

⬅️ **[Previous: Chapter 4 - Importing Your Own Code](chapter-04.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 6 - Pygame Development](chapter-06.md)**
