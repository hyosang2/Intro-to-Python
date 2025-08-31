---
layout: default
title: Chapter 6 - Turtle Graphics
---

# Chapter 6: Turtle Basics

**Turtle** is a fun Python library that lets you draw pictures and create graphics using simple commands. It's like having a digital pen that you can control with code! The turtle starts in the center of the screen and follows your commands to draw lines, shapes, and colorful patterns. As mentioned in Chapter 5, Turtle comes built-in with Python through the import system.

Turtle comes built-in with Python, so you don't need to install anything extra. It's perfect for learning programming because you can see your code come to life as drawings on the screen. This visual feedback makes it an excellent bridge between the object-oriented concepts you learned in Chapters 2 through 4 and practical programming applications.

## Basic Turtle Commands

Let's start with the most important turtle commands. Think of the turtle as a little robot that can move around and draw:

```python
import turtle

# Create a turtle and a screen
my_turtle = turtle.Turtle()
screen = turtle.Screen()

# Basic movement commands
my_turtle.forward(100)    # Move forward 100 steps
my_turtle.right(90)       # Turn right 90 degrees
my_turtle.forward(50)     # Move forward 50 steps
my_turtle.left(45)        # Turn left 45 degrees
my_turtle.backward(75)    # Move backward 75 steps

# Keep the window open until clicked
screen.exitonclick()
```

This code creates a simple path that the turtle draws. When you run it, you'll see a window open with lines showing where the turtle moved!

## Drawing Shapes

One of the most fun things about turtle is drawing shapes. Let's create some basic shapes:

```python
import turtle

# Create turtle
artist = turtle.Turtle()
screen = turtle.Screen()

# Draw a square
for i in range(4):
    artist.forward(100)
    artist.right(90)

# Move to a new position without drawing
artist.penup()           # Lift the pen
artist.goto(150, 0)      # Move to position (150, 0)
artist.pendown()         # Put the pen down

# Draw a triangle
for i in range(3):
    artist.forward(80)
    artist.right(120)

screen.exitonclick()
```

Here we use loops to draw shapes efficiently. The square uses 4 sides with 90-degree turns, and the triangle uses 3 sides with 120-degree turns.

## Colors and Pen Control

Let's make our drawings more colorful and interesting:

```python
import turtle

# Create turtle
painter = turtle.Turtle()
screen = turtle.Screen()
screen.bgcolor("lightblue")  # Set background color

# Set turtle properties
painter.color("red")         # Set pen color
painter.pensize(5)           # Make lines thicker
painter.speed(3)             # Set drawing speed (1-10)

# Draw a colorful flower
for i in range(6):
    painter.circle(50)       # Draw a circle with radius 50
    painter.right(60)        # Turn to create petal pattern

# Change color and draw the stem
painter.color("green")
painter.pensize(8)
painter.right(90)
painter.forward(150)

screen.exitonclick()
```

**Output:**
```
# This creates a beautiful flower drawing with:
# - Light blue background
# - Red flower petals (6 circles)
# - Green stem
# - Thick lines for better visibility
```

### Understanding Colors

In Python graphics, there are two main ways to specify colors:

**Color Names**: Python knows many color names that you can use as strings. These are easy to remember and use:

```python
# Using color names (easy to remember!)
turtle.color("red")
turtle.color("blue")
turtle.color("green")
turtle.color("purple")
turtle.color("orange")
turtle.color("pink")
turtle.color("yellow")
turtle.color("lightblue")
turtle.color("darkgreen")
```

**RGB Colors**: RGB stands for Red, Green, Blue. Every color on your computer screen is made by mixing these three colors. You specify how much of each color to use with numbers from 0 to 255:

```python
import turtle

# Set up screen to use RGB mode
screen = turtle.Screen()
screen.colormode(255)  # Tell turtle to use 0-255 for colors

artist = turtle.Turtle()

# RGB colors: (Red, Green, Blue)
artist.color((255, 0, 0))    # Pure red
artist.forward(50)

artist.color((0, 255, 0))    # Pure green  
artist.forward(50)

artist.color((0, 0, 255))    # Pure blue
artist.forward(50)

artist.color((255, 255, 0))  # Red + Green = Yellow
artist.forward(50)

artist.color((255, 0, 255))  # Red + Blue = Magenta
artist.forward(50)

artist.color((128, 64, 200)) # Custom purple color
artist.forward(50)

screen.exitonclick()
```

**Output:**
```
# This creates a line with 6 different colored segments:
# - Pure red
# - Pure green  
# - Pure blue
# - Yellow (red + green)
# - Magenta (red + blue)
# - Custom purple
```

Understanding RGB colors is important because more advanced graphics libraries like Pygame (which we'll explore in Chapter 7) use the same system! In RGB:
- `(0, 0, 0)` = Black (no colors)
- `(255, 255, 255)` = White (all colors at maximum)
- `(255, 0, 0)` = Red
- `(0, 255, 0)` = Green
- `(0, 0, 255)` = Blue

## Turtle and Object-Oriented Programming

Here's where turtle connects to what we've learned about OOP in Chapters 2 through 4! Each turtle is actually an object with its own properties and methods, demonstrating the concepts of classes and objects in action:

```python
import turtle

class DrawingTurtle:
    def __init__(self, name, color, size):
        self.name = name
        self.turtle = turtle.Turtle()
        self.turtle.color(color)
        self.turtle.pensize(size)
        self.turtle.speed(5)
        print(f"Created turtle named {self.name} with {color} color!")
    
    def draw_square(self, side_length):
        print(f"{self.name} is drawing a square!")
        for i in range(4):
            self.turtle.forward(side_length)
            self.turtle.right(90)
    
    def draw_circle(self, radius):
        print(f"{self.name} is drawing a circle!")
        self.turtle.circle(radius)
    
    def move_to(self, x, y):
        self.turtle.penup()
        self.turtle.goto(x, y)
        self.turtle.pendown()

# Create turtle objects
artist1 = DrawingTurtle("Pablo", "blue", 3)
artist2 = DrawingTurtle("Penny", "purple", 5)

# Set up screen
screen = turtle.Screen()
screen.setup(800, 600)

# Use our turtle objects
artist1.draw_square(80)
artist1.move_to(200, 100)
artist1.draw_circle(40)

artist2.move_to(-200, -100)
artist2.draw_square(60)

screen.exitonclick()
```

**Output:**
```
Created turtle named Pablo with blue color!
Created turtle named Penny with purple color!
Pablo is drawing a square!
Pablo is drawing a circle!
Penny is drawing a square!
```

## Interactive Turtle Programs

We can make turtle respond to keyboard input, creating interactive drawings:

```python
import turtle

class ControllableTurtle:
    def __init__(self):
        self.turtle = turtle.Turtle()
        self.turtle.color("orange")
        self.turtle.pensize(3)
        self.turtle.speed(6)
        
        # Set up the screen
        self.screen = turtle.Screen()
        self.screen.setup(600, 600)
        self.screen.title("Control the Turtle with Arrow Keys!")
        
        # Bind keys to methods
        self.screen.onkey(self.move_up, "Up")
        self.screen.onkey(self.move_down, "Down")
        self.screen.onkey(self.move_left, "Left")
        self.screen.onkey(self.move_right, "Right")
        self.screen.onkey(self.change_color, "space")
        
        # Listen for key presses
        self.screen.listen()
        
        self.colors = ["red", "blue", "green", "purple", "orange", "yellow"]
        self.color_index = 0
    
    def move_up(self):
        self.turtle.setheading(90)   # Point up
        self.turtle.forward(20)
    
    def move_down(self):
        self.turtle.setheading(270)  # Point down
        self.turtle.forward(20)
    
    def move_left(self):
        self.turtle.setheading(180)  # Point left
        self.turtle.forward(20)
    
    def move_right(self):
        self.turtle.setheading(0)    # Point right
        self.turtle.forward(20)
    
    def change_color(self):
        self.color_index = (self.color_index + 1) % len(self.colors)
        self.turtle.color(self.colors[self.color_index])
        print(f"Color changed to {self.colors[self.color_index]}!")

# Create and use the controllable turtle
my_turtle = ControllableTurtle()
print("Use arrow keys to move, spacebar to change colors!")
my_turtle.screen.exitonclick()
```

**Output:**
```
Use arrow keys to move, spacebar to change colors!
Color changed to blue!
Color changed to green!
# (Output appears as you press keys)
```

## Displaying Text with Turtle

Sometimes you want to add text to your drawings to create labels, titles, or messages. Turtle makes this easy with the `write()` method:

```python
import turtle

# Create turtle and set up screen
writer = turtle.Turtle()
screen = turtle.Screen()
screen.bgcolor("lightgreen")

# Hide the turtle shape (we just want text)
writer.hideturtle()

# Write text at different positions
writer.goto(-200, 200)
writer.write("Welcome to Turtle Graphics!", font=("Arial", 24, "bold"))

writer.goto(-150, 150)
writer.color("blue")
writer.write("This is blue text", font=("Times", 16, "normal"))

writer.goto(-100, 100)
writer.color("red")
writer.write("RED ALERT!", font=("Courier", 20, "bold"))

# Move and write with different alignments
writer.goto(0, 0)
writer.color("purple")
writer.write("Centered text", align="center", font=("Arial", 14, "italic"))

writer.goto(100, -50)
writer.color("darkgreen")
writer.write("Right aligned", align="right", font=("Arial", 12, "normal"))

screen.exitonclick()
```

**Output:**
```
# This creates a window with various text examples:
# - Large bold title at the top
# - Blue text in Times font
# - Red alert message in Courier font
# - Purple centered text
# - Dark green right-aligned text
```

The `write()` method has several useful options:
- `font=("FontName", size, "style")` - Controls text appearance
- `align="left"/"center"/"right"` - Controls text alignment
- `move=True/False` - Whether turtle moves after writing (default False)

You can also create interactive text that changes based on user input:

```python
import turtle

class TextDisplay:
    def __init__(self):
        self.screen = turtle.Screen()
        self.screen.setup(600, 400)
        self.screen.bgcolor("white")
        
        self.writer = turtle.Turtle()
        self.writer.hideturtle()
        self.writer.speed(0)
        
        self.score = 0
        self.update_display()
        
        # Set up key bindings
        self.screen.onkey(self.increase_score, "Up")
        self.screen.onkey(self.decrease_score, "Down")
        self.screen.listen()
    
    def update_display(self):
        self.writer.clear()  # Clear previous text
        self.writer.goto(0, 100)
        self.writer.write(f"Score: {self.score}", align="center", 
                         font=("Arial", 36, "bold"))
        
        self.writer.goto(0, 50)
        self.writer.write("Use UP/DOWN arrows to change score", 
                         align="center", font=("Arial", 14, "normal"))
    
    def increase_score(self):
        self.score += 10
        self.update_display()
    
    def decrease_score(self):
        self.score -= 5
        self.update_display()

# Create interactive text display
game = TextDisplay()
game.screen.exitonclick()
```

**Output:**
```
Score: 0
Use UP/DOWN arrows to change score
# Score changes as you press arrow keys!
```

## Understanding Keyboard Input in Turtle

Turtle can respond to keyboard input, making your programs interactive! Here's how keyboard input works:

```python
import turtle

# Set up turtle and screen
my_turtle = turtle.Turtle()
screen = turtle.Screen()
screen.setup(400, 300)

# Functions to control the turtle
def move_up():
    my_turtle.setheading(90)    # Point up
    my_turtle.forward(20)

def move_down():
    my_turtle.setheading(270)   # Point down  
    my_turtle.forward(20)

def draw_circle():
    my_turtle.circle(25)

def change_color():
    my_turtle.color("red")

# Connect keys to functions
screen.onkey(move_up, "Up")      # Arrow key
screen.onkey(move_down, "Down")  # Arrow key
screen.onkey(draw_circle, "c")   # Letter key (lowercase!)
screen.onkey(change_color, "space")  # Space bar

# Start listening for key presses
screen.listen()  # This is very important!

print("Use arrow keys to move, 'c' for circle, space for red color")
screen.exitonclick()
```

**Output:**
```
Use arrow keys to move, 'c' for circle, space for red color
# Turtle responds when you press the keys!
```

**Key Rules for Keyboard Input:**
- Call `screen.listen()` to start receiving key presses
- Use lowercase for letter keys: "a", "b", "c" (not "A", "B", "C")
- Arrow keys: "Up", "Down", "Left", "Right"
- Special keys: "space", "Return" (Enter), "Delete"
- Click the turtle window to make it active for keyboard input

## Creating Art with Turtle

Let's combine everything we've learned to create a beautiful spiral pattern:

```python
import turtle
import random

class SpiralArtist:
    def __init__(self):
        self.turtle = turtle.Turtle()
        self.screen = turtle.Screen()
        self.screen.bgcolor("black")
        self.screen.setup(800, 800)
        self.turtle.speed(0)  # Fastest speed
        
        self.colors = ["red", "orange", "yellow", "green", "blue", "purple", "pink", "cyan"]
    
    def draw_colorful_spiral(self):
        for i in range(200):
            # Pick a random color
            color = random.choice(self.colors)
            self.turtle.color(color)
            
            # Draw and turn
            self.turtle.forward(i * 2)
            self.turtle.right(91)  # Slightly more than 90 degrees creates spiral
    
    def draw_rainbow_flower(self, petals=12):
        for i in range(petals):
            # Use different colors for each petal
            color = self.colors[i % len(self.colors)]
            self.turtle.color(color)
            
            # Draw petal
            self.turtle.circle(100)
            self.turtle.right(360 / petals)

# Create spiral art
artist = SpiralArtist()
print("Creating colorful spiral art...")
artist.draw_colorful_spiral()

# Reset position for flower
artist.turtle.home()
artist.turtle.clear()

print("Creating rainbow flower...")
artist.draw_rainbow_flower()

artist.screen.exitonclick()
```

**Output:**
```
Creating colorful spiral art...
Creating rainbow flower...
```

Turtle graphics provide an excellent bridge between basic programming concepts and visual creativity. You can see your code come to life as colorful drawings, making it perfect for understanding how programming instructions translate into visual results.

The turtle library demonstrates many OOP concepts we've learned:
- Each turtle is an **object** with its own state (position, color, direction) as explained in Chapter 3
- Turtle methods like `forward()`, `color()`, and `circle()` are **instance methods** as covered in Chapter 2
- We can create custom turtle classes that **inherit** from or use turtle objects, applying inheritance concepts from Chapter 4
- Different turtle objects can have different behaviors (**polymorphism**) as demonstrated in Chapter 4

This foundation in turtle graphics prepares you perfectly for the more advanced game development concepts we'll explore with Pygame in Chapter 7!

---

## Navigation

⬅️ **[Previous: Chapter 5 - Import and Modules](chapter-05.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 7 - Pygame Development](chapter-07.md)**