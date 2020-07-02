---
title: "Working with pygame - 1"
excerpt: "Learning to use pygame"
date: 2020-07-02
---

### pygame Library

- The first thing to do is to import pygame and initialize it.

```python
import pygame

pygame.init()
```

### Colors

- Next, we need to add variables that define our program's colors. Colors are defined in a list of three colors: red, green, and blue.
- Each element of the RGB triad is a number ranging from 0 to 255.
  - Zero means there is none of the color.
  - 255 tells the monitor to display as much of the color as possible.
  - The colors combine in an additive way, so if all three colors are specified, the color on the monitor appears **white**.
- We'll use a list to define colors. We don't expect the colors to change so use upper-case.
- If we do expect the color to change then we'll use lower-case e.g. color of the sky so variable name will be **color_sky**.
- Drawing arcs is important so we need pi. Declare it: **PI = 3.141592653** or import it from the math library as math.pi.

```python
# Define some colors
BLACK    = (   0,   0,   0)
WHITE    = ( 255, 255, 255)
GREEN    = (   0, 255,   0)
RED      = ( 255,   0,   0)
BLUE     = (   0,   0, 255)
```

### Opening a window

- Size is yet again a list.
- Set mode can do a lot e.g. run full screen, etc.
- The code for opening a window is given below.

```python
size = (700, 500)
screen = pygame.display.set_mode(size)
pygame.display.set_caption("Window Name - GHOST OF TSUSHIMA")
```

### Setting up the Main Loop

A lot to unpack here but basically boils down to this:
  - Main loop until user says exit.
  - 'Main Event Loop' to get inputs from user.
  - 'Game Logic area' to build the actual logic of the game.
  - 'Drawing code' - what to show on the screen.

```python
# Loop until the user clicks the close button.
done = False

# Used to manage how fast the screen updates
clock = pygame.time.Clock()

# -------- Main Program Loop -----------
while not done:
    # --- Main event loop
    for event in pygame.event.get(): # User did something
        if event.type == pygame.QUIT: # If user clicked close
            done = True # Flag that we are done so we exit this loop

    # --- Game logic should go here

    # --- Drawing code should go here

    # First, clear the screen to white. Don't put other drawing commands
    # above this, or they will be erased with this command.
    screen.fill(WHITE)

    # --- Go ahead and update the screen with what we've drawn.
    pygame.display.flip()

    # --- Limit to 60 frames per second
    clock.tick(60)
```
