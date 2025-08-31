---
layout: default
title: Chapter 7 - Pygame Development
---

# Chapter 7: Pygame Basics

Now that you've learned how to create drawings with Turtle graphics in Chapter 6, you're ready for the next level: game development! **Pygame** is a Python library for creating games and multimedia applications. It provides tools for graphics, sound, and game logic. While Turtle is great for simple drawings, Pygame lets you create interactive games with moving objects, sound effects, and complex animations.

Pygame uses object-oriented programming extensively, making it perfect for applying all the OOP concepts you've learned in Chapters 2 through 4, including classes, objects, inheritance, and polymorphism.

Before using Pygame, install it with: `pip install pygame`. Like other Python libraries discussed in Chapter 5, Pygame must be imported before use.

## Sprites

A **sprite** in Pygame is a 2D image or animation that can be moved around the screen. In Pygame, sprites are implemented as classes that inherit from `pygame.sprite.Sprite`, demonstrating the inheritance principle covered in Chapter 4.

```python
import pygame

class Spaceship(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        # Create a simple colored rectangle for our spaceship
        self.image = pygame.Surface((40, 30))
        self.image.fill((0, 255, 0))  # Green spaceship
        
        # Get rectangle for positioning
        self.rect = self.image.get_rect()
        self.rect.center = (400, 500)  # Start at bottom center
    
    def update(self):
        # Move the spaceship with arrow keys
        keys = pygame.key.get_pressed()
        if keys[pygame.K_LEFT]:
            self.rect.x -= 5
        if keys[pygame.K_RIGHT]:
            self.rect.x += 5
        if keys[pygame.K_UP]:
            self.rect.y -= 5
        if keys[pygame.K_DOWN]:
            self.rect.y += 5
        
        # Keep spaceship on screen
        if self.rect.left < 0:
            self.rect.left = 0
        if self.rect.right > 800:
            self.rect.right = 800
```

### Sprite.rect

The `rect` attribute is crucial for sprite positioning and collision detection. It's a `pygame.Rect` object that represents the sprite's position and size.

```python
# Common rect properties for positioning
spaceship.rect.x = 100        # Left edge position
spaceship.rect.y = 50         # Top edge position
spaceship.rect.center = (400, 300)     # Center position
spaceship.rect.bottom = 600   # Bottom edge position
spaceship.rect.right = 800    # Right edge position

# Size properties
spaceship.rect.width = 40     # Width in pixels
spaceship.rect.height = 30    # Height in pixels
```

### Sprite Groups

**Sprite groups** are containers that hold multiple sprites. They make it easy to update and draw many sprites at once.

```python
# Create sprite groups
all_sprites = pygame.sprite.Group()
asteroids = pygame.sprite.Group()

# Add sprites to groups
spaceship = Spaceship()
asteroid1 = Asteroid()
asteroid2 = Asteroid()

all_sprites.add(spaceship, asteroid1, asteroid2)
asteroids.add(asteroid1, asteroid2)

# Update all sprites in groups
all_sprites.update()

# Draw all sprites in groups
all_sprites.draw(screen)
```

## Game Loops

Every Pygame game needs a **game loop** (also called a **running loop**) that continuously updates the game state and redraws the screen.

```python
import pygame

# Initialize Pygame
pygame.init()

# Set up the display
screen = pygame.display.set_mode((800, 600))
pygame.display.set_caption("Space Adventure!")
clock = pygame.time.Clock()

# Create sprite groups
all_sprites = pygame.sprite.Group()
spaceship = Spaceship()
all_sprites.add(spaceship)

# Game loop
running = True
while running:
    # Handle events (like closing the window)
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
    
    # Update all sprites
    all_sprites.update()
    
    # Draw everything
    screen.fill((0, 0, 50))  # Dark blue space background
    all_sprites.draw(screen)
    
    # Update the display
    pygame.display.flip()
    clock.tick(60)  # 60 frames per second

pygame.quit()
```

## Draw and Blit

**Drawing** and **blitting** are fundamental Pygame operations for displaying graphics.

**Drawing** creates shapes directly on surfaces:
```python
# Draw space objects on screen
pygame.draw.circle(screen, (255, 255, 0), (100, 100), 30)    # Yellow sun
pygame.draw.rect(screen, (255, 0, 0), (200, 200, 40, 60))    # Red asteroid
pygame.draw.line(screen, (255, 255, 255), (0, 0), (800, 600), 2)  # White laser
```

**Blitting** copies one surface onto another:
```python
# Load space images
spaceship_image = pygame.image.load("spaceship.png")
star_image = pygame.image.load("star.png")

# Blit (copy) images to screen
screen.blit(spaceship_image, (400, 500))  # Spaceship at bottom center
screen.blit(star_image, (50, 50))         # Star in top left

# You can also blit part of an image (useful for animation)
screen.blit(spaceship_image, (400, 500), (0, 0, 32, 32))  # Only 32x32 part
```

Here's a simple complete space game example:

```python
import pygame
import random

class Star(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface((3, 3))
        self.image.fill((255, 255, 255))  # White star
        self.rect = self.image.get_rect()
        self.rect.x = random.randint(0, 800)
        self.rect.y = random.randint(0, 600)

# Create stars for background
stars = pygame.sprite.Group()
for i in range(50):
    star = Star()
    stars.add(star)

# In your game loop:
# stars.draw(screen)  # Draw twinkling stars
```

Pygame combines OOP principles with game development, allowing you to create engaging space adventures and other interactive applications using the concepts learned in this guide.

## Displaying Text in Pygame

Just like with Turtle graphics (see Chapter 6), displaying text is an important part of creating games. You might want to show scores, messages, instructions, or game titles. Pygame uses fonts to render text, building on the color concepts you learned with Turtle.

Remember from Chapter 6 in the Turtle section that colors can be specified as RGB tuples like `(255, 0, 0)` for red? Pygame uses the exact same RGB color system!

```python
import pygame

# Initialize Pygame and create screen
pygame.init()
screen = pygame.display.set_mode((800, 600))
pygame.display.set_caption("Space Adventure - Text Demo")

# Create fonts (different sizes and styles)
title_font = pygame.font.Font(None, 48)     # Large font for titles
score_font = pygame.font.Font(None, 36)     # Medium font for scores
info_font = pygame.font.Font(None, 24)      # Small font for info

# Define colors (same RGB system as Turtle!)
WHITE = (255, 255, 255)
RED = (255, 0, 0)
GREEN = (0, 255, 0)
BLUE = (0, 0, 255)
YELLOW = (255, 255, 0)
PURPLE = (255, 0, 255)
ORANGE = (255, 165, 0)
SPACE_BLUE = (0, 0, 50)

# Create text surfaces
title_text = title_font.render("SPACE ADVENTURE", True, YELLOW)
score_text = score_font.render("Score: 1250", True, WHITE)
health_text = score_font.render("Health: 100%", True, GREEN)
warning_text = info_font.render("Asteroid approaching!", True, RED)
info_text = info_font.render("Use arrow keys to move", True, WHITE)

# Game loop
clock = pygame.time.Clock()
running = True

while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
    
    # Fill background
    screen.fill(SPACE_BLUE)
    
    # Display text at different positions
    screen.blit(title_text, (250, 50))      # Title at top
    screen.blit(score_text, (50, 100))      # Score in top left
    screen.blit(health_text, (600, 100))    # Health in top right
    screen.blit(warning_text, (300, 300))   # Warning in center
    screen.blit(info_text, (250, 550))      # Instructions at bottom
    
    pygame.display.flip()
    clock.tick(60)

pygame.quit()
```

This creates a game window with:
- Yellow "SPACE ADVENTURE" title at the top
- White score display in top left
- Green health display in top right  
- Red warning message in the center
- White instructions at the bottom

You can also create dynamic text that changes during gameplay:

```python
import pygame
import random

class GameUI:
    def __init__(self, screen):
        self.screen = screen
        self.font = pygame.font.Font(None, 36)
        self.small_font = pygame.font.Font(None, 24)
        
        # Game state
        self.score = 0
        self.lives = 3
        self.level = 1
        
        # Colors
        self.WHITE = (255, 255, 255)
        self.RED = (255, 0, 0)
        self.GREEN = (0, 255, 0)
        self.YELLOW = (255, 255, 0)
    
    def update_score(self, points):
        self.score += points
        if self.score > 0 and self.score % 500 == 0:  # Level up every 500 points
            self.level += 1
    
    def lose_life(self):
        self.lives -= 1
    
    def draw(self):
        # Score display
        score_text = self.font.render(f"Score: {self.score}", True, self.WHITE)
        self.screen.blit(score_text, (10, 10))
        
        # Lives display (changes color based on remaining lives)
        lives_color = self.GREEN if self.lives > 1 else self.RED
        lives_text = self.font.render(f"Lives: {self.lives}", True, lives_color)
        self.screen.blit(lives_text, (10, 50))
        
        # Level display
        level_text = self.font.render(f"Level: {self.level}", True, self.YELLOW)
        self.screen.blit(level_text, (10, 90))
        
        # Game over message
        if self.lives <= 0:
            game_over = self.font.render("GAME OVER", True, self.RED)
            restart_text = self.small_font.render("Press R to restart", True, self.WHITE)
            
            # Center the text
            game_over_rect = game_over.get_rect(center=(400, 300))
            restart_rect = restart_text.get_rect(center=(400, 340))
            
            self.screen.blit(game_over, game_over_rect)
            self.screen.blit(restart_text, restart_rect)

# Usage in game loop:
# ui = GameUI(screen)
# ui.update_score(50)  # Add 50 points
# ui.draw()           # Display UI
```

**Output:**
```
Score: 1250
Lives: 2
Level: 3
# Text colors change based on game state!
```

## Understanding Keyboard Input in Pygame

Pygame handles keyboard input differently than Turtle, with two main approaches for different types of controls:

```python
import pygame

# Initialize pygame
pygame.init()
screen = pygame.display.set_mode((600, 400))
pygame.display.set_caption("Spaceship Controls")

# Spaceship position and colors
ship_x, ship_y = 300, 200
BLACK = (0, 0, 0)
GREEN = (0, 255, 0)
WHITE = (255, 255, 255)

clock = pygame.time.Clock()
font = pygame.font.Font(None, 24)

running = True
while running:
    # Handle single key presses (events)
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_SPACE:
                print("Fired laser!")
    
    # Handle held-down keys (continuous movement)
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        ship_x -= 5
    if keys[pygame.K_RIGHT]:
        ship_x += 5
    if keys[pygame.K_UP]:
        ship_y -= 5
    if keys[pygame.K_DOWN]:
        ship_y += 5
    
    # Keep ship on screen
    ship_x = max(0, min(600, ship_x))
    ship_y = max(0, min(400, ship_y))
    
    # Draw everything
    screen.fill(BLACK)
    pygame.draw.rect(screen, GREEN, (ship_x-15, ship_y-10, 30, 20))
    
    text = font.render("Arrow keys to move, Space to fire", True, WHITE)
    screen.blit(text, (10, 10))
    
    pygame.display.flip()
    clock.tick(60)

pygame.quit()
```

**Output:**
```
Arrow keys to move, Space to fire
Fired laser!
Fired laser!
# Ship moves smoothly with arrow keys!
```

**Key Differences from Turtle (Chapter 6):**
- **Two input types**: Events (single presses) vs continuous (held keys)
- **No listen() needed**: Pygame handles keyboard automatically
- **Key constants**: Use `pygame.K_LEFT` instead of "Left"
- **Game loop**: Check input every frame in the main loop

These examples show how Pygame builds on the foundation you learned with Turtle graphics in Chapter 6, using the same RGB color system and similar concepts for handling user input, but with much more power and flexibility for creating complete games! The object-oriented principles from Chapters 2 through 4 become essential for organizing complex game code with multiple sprites, game states, and interactive elements.

---

## Navigation

⬅️ **[Previous: Chapter 6 - Turtle Graphics](chapter-06.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

🎉 **You've completed the Python OOP Guide!**