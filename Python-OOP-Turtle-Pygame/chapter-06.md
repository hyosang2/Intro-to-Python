---
layout: default
title: Chapter 6 - Pygame Development
---

# Chapter 6: Pygame Development

Now that you've created drawings with Turtle, you're ready for the next level: game development! **Pygame** is a Python library for creating games with moving objects, sound effects, and animations. It uses OOP extensively, making it perfect for applying the concepts from Chapters 2–3.

Before using Pygame, install it with: `pip install pygame`

## The Game Loop

Every Pygame game follows the same core structure — a **game loop** that runs continuously, handling input, updating game state, and drawing to the screen:

```python
import pygame

# Initialize Pygame
pygame.init()

# Set up the display
screen = pygame.display.set_mode((800, 600))
pygame.display.set_caption("My First Game")
clock = pygame.time.Clock()

# Game loop
running = True
while running:
    # 1. Handle events (input, window close)
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # 2. Update game state
    # (move objects, check collisions, etc.)

    # 3. Draw everything
    screen.fill((0, 0, 50))       # Dark blue background
    pygame.display.flip()          # Show the new frame
    clock.tick(60)                 # 60 frames per second

pygame.quit()
```

This loop runs roughly 60 times per second, creating the illusion of smooth movement. Pygame uses the same **RGB color system** as Turtle (Chapter 5) — for example, `(255, 0, 0)` is red and `(0, 0, 0)` is black.

## Sprites

A **sprite** is a game object (a character, enemy, bullet, etc.) represented by an image or shape that can move around the screen. In Pygame, sprites are classes that inherit from `pygame.sprite.Sprite`, demonstrating **inheritance** from Chapter 3:

```python
import pygame

class Spaceship(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface((40, 30))
        self.image.fill((0, 255, 0))        # Green rectangle
        self.rect = self.image.get_rect()
        self.rect.center = (400, 500)        # Start position
        self.speed = 5

    def update(self):
        keys = pygame.key.get_pressed()
        if keys[pygame.K_LEFT]:
            self.rect.x -= self.speed
        if keys[pygame.K_RIGHT]:
            self.rect.x += self.speed
        if keys[pygame.K_UP]:
            self.rect.y -= self.speed
        if keys[pygame.K_DOWN]:
            self.rect.y += self.speed

        # Keep on screen
        self.rect.clamp_ip(screen.get_rect())
```

Every sprite has two essential attributes: **`self.image`** (what it looks like) and **`self.rect`** (its position and size as a rectangle).

### The `rect` Object

The `rect` attribute is a `pygame.Rect` that stores the sprite's position and size. It has many useful properties:

```python
spaceship.rect.x              # Left edge
spaceship.rect.y              # Top edge
spaceship.rect.center         # (x, y) of center
spaceship.rect.width          # Width in pixels
spaceship.rect.bottom         # Bottom edge
spaceship.rect.right          # Right edge
```

### Sprite Groups

**Sprite groups** hold multiple sprites and let you update and draw them all at once:

```python
all_sprites = pygame.sprite.Group()
enemies = pygame.sprite.Group()

spaceship = Spaceship()
all_sprites.add(spaceship)

# In the game loop:
all_sprites.update()           # Calls update() on every sprite
all_sprites.draw(screen)       # Draws every sprite to the screen
```

## Drawing and Blitting

**Drawing** creates shapes directly on the screen:

```python
pygame.draw.circle(screen, (255, 255, 0), (100, 100), 30)         # Yellow circle
pygame.draw.rect(screen, (255, 0, 0), (200, 200, 40, 60))         # Red rectangle
pygame.draw.line(screen, (255, 255, 255), (0, 0), (800, 600), 2)  # White line
```

**Blitting** copies an image onto the screen:

```python
spaceship_img = pygame.image.load("spaceship.png")
screen.blit(spaceship_img, (400, 500))
```

## Collision Detection

Collision detection tells you when two objects touch — essential for any game. Pygame makes this easy with sprite groups:

```python
import pygame
import random

class Asteroid(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface((20, 20))
        self.image.fill((150, 75, 0))     # Brown
        self.rect = self.image.get_rect()
        self.rect.x = random.randint(0, 780)
        self.rect.y = random.randint(-100, -10)
        self.speed = random.randint(2, 6)

    def update(self):
        self.rect.y += self.speed
        if self.rect.top > 600:           # Fell off the bottom
            self.rect.y = random.randint(-100, -10)
            self.rect.x = random.randint(0, 780)
```

To check if the spaceship hits any asteroid:

```python
# Check collisions between one sprite and a group
hits = pygame.sprite.spritecollide(spaceship, asteroids, True)
# True means: remove the asteroid from the group when hit

if hits:
    print(f"Hit {len(hits)} asteroid(s)!")
```

You can also check collisions between two individual rects:

```python
if spaceship.rect.colliderect(asteroid.rect):
    print("Collision!")
```

## Displaying Text

Pygame uses **fonts** to render text as images, then blits them to the screen:

```python
font = pygame.font.Font(None, 36)      # Default font, size 36
text_surface = font.render("Score: 100", True, (255, 255, 255))
screen.blit(text_surface, (10, 10))
```

To center text:

```python
text_surface = font.render("GAME OVER", True, (255, 0, 0))
text_rect = text_surface.get_rect(center=(400, 300))
screen.blit(text_surface, text_rect)
```

## Keyboard Input

Pygame handles keyboard input in two ways:

**Events** — for single key presses (fires once per press):

```python
for event in pygame.event.get():
    if event.type == pygame.KEYDOWN:
        if event.key == pygame.K_SPACE:
            print("Fire!")
```

**Continuous** — for held-down keys (checked every frame):

```python
keys = pygame.key.get_pressed()
if keys[pygame.K_LEFT]:
    ship_x -= 5
if keys[pygame.K_RIGHT]:
    ship_x += 5
```

Use events for actions like shooting or pausing, and continuous input for smooth movement. Unlike Turtle, Pygame doesn't need `listen()` — input handling is built into the game loop.

## Putting It All Together

Here's a mini space game that combines sprites, collision detection, text, and input:

```python
import pygame
import random

pygame.init()
screen = pygame.display.set_mode((800, 600))
pygame.display.set_caption("Space Dodge!")
clock = pygame.time.Clock()
font = pygame.font.Font(None, 36)

class Ship(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface((40, 30))
        self.image.fill((0, 255, 0))
        self.rect = self.image.get_rect(center=(400, 550))

    def update(self):
        keys = pygame.key.get_pressed()
        if keys[pygame.K_LEFT]:
            self.rect.x -= 5
        if keys[pygame.K_RIGHT]:
            self.rect.x += 5
        self.rect.clamp_ip(screen.get_rect())

class Rock(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface((20, 20))
        self.image.fill((150, 75, 0))
        self.rect = self.image.get_rect()
        self.reset()

    def reset(self):
        self.rect.x = random.randint(0, 780)
        self.rect.y = random.randint(-200, -20)
        self.speed = random.randint(3, 7)

    def update(self):
        self.rect.y += self.speed
        if self.rect.top > 600:
            self.reset()

# Create sprites
ship = Ship()
all_sprites = pygame.sprite.Group(ship)
rocks = pygame.sprite.Group()
for i in range(8):
    rock = Rock()
    all_sprites.add(rock)
    rocks.add(rock)

score = 0
running = True

while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    all_sprites.update()
    score += 1

    # Check collisions
    if pygame.sprite.spritecollide(ship, rocks, False):
        running = False  # Game over!

    # Draw
    screen.fill((0, 0, 30))
    all_sprites.draw(screen)
    text = font.render(f"Score: {score}", True, (255, 255, 255))
    screen.blit(text, (10, 10))
    pygame.display.flip()
    clock.tick(60)

# Game over screen
screen.fill((0, 0, 0))
game_over_text = font.render(f"Game Over! Final Score: {score}", True, (255, 0, 0))
text_rect = game_over_text.get_rect(center=(400, 300))
screen.blit(game_over_text, text_rect)
pygame.display.flip()
pygame.time.wait(3000)
pygame.quit()
```

This game demonstrates nearly every OOP concept from this guide: **classes** (Ship, Rock), **inheritance** (from `pygame.sprite.Sprite`), **polymorphism** (each sprite's `update()` behaves differently), **encapsulation** (each sprite manages its own state), and **abstraction** (you call `all_sprites.update()` without worrying about the details).

Try it yourself! Add a `Bullet` class that the ship fires when the player presses the spacebar. Check for collisions between bullets and rocks to let the player destroy them.

---

## Navigation

⬅️ **[Previous: Chapter 5 - Turtle Graphics](chapter-05.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

🎉 **You've completed the Python OOP Guide!**
