---
title: "Working with pygame - 1"
excerpt: "Learning to use pygame"
date: 2020-07-03
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

- Size is tupple here. It is not changable. If you want changeable values, use a list: **[800, 600]**
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

### Drawing Lines

- The code examples below shows how to draw a lines on the screen.
- Attributes are (screen, color, [x1, y1], [x2, y2], thickness)

```python
#Drawing a single line
# Draw on the screen a green line from (0, 0) to (100, 100)
# that is 5 pixels wide.
pygame.draw.line(screen, GREEN, [0, 0], [100, 100], 5)


# Draw on the screen several lines from (0, 10) to (100, 110)
# 5 pixels wide using a while loop
y_offset = 0
while y_offset < 100:
    pygame.draw.line(screen,RED,[0,10+y_offset],[100,110+y_offset],5)
    y_offset = y_offset + 10

# Same code as above but with for
# Draw on the screen several lines from (0,10) to (100,110)
# 5 pixels wide using a for loop
for y_offset in range(0, 100, 10):
    pygame.draw.line(screen,RED,[0,10+y_offset],[100,110+y_offset],5)    
```

- Lines can be drawn in more complex styles as shown below. This will print a series of x's on the screen.

```python
# Drawing a series of x's
for x_offset in range(30, 300, 30):
    pygame.draw.line(screen,BLACK,[x_offset,100],[x_offset-10,90],2)
    pygame.draw.line(screen,BLACK,[x_offset,90],[x_offset-10,100],2)
```

### Drawing Rectangles and Ellipses

- Pretty simple stuff. Attributes are (screen, color, [x, y, width, height], thickness).

```python
# Rectangle
pygame.draw.rect(screen,BLACK,[20,20,250,100],2)

# Ellipse
pygame.draw.ellipse(screen, BLACK, [20,20,250,100], 2)
```

### Drawing Arcs

- Arc is contained within a rectangle.
- [x, y, width, height] is the starting point, width and the height of the rectangle in which the arc will be drawn.
- The PI attributes are where to start and where to end.
- Attributes are (screen, color, [x, y, width, height], start, end)

```python
# Draw an arc as part of an ellipse. Use radians to determine what
# angle to draw.
pygame.draw.arc(screen, GREEN, [100,100,250,200],  PI/2,     PI, 2)
pygame.draw.arc(screen, BLACK, [100,100,250,200],     0,   PI/2, 2)
pygame.draw.arc(screen, RED,   [100,100,250,200],3*PI/2,   2*PI, 2)
pygame.draw.arc(screen, BLUE,  [100,100,250,200],    PI, 3*PI/2, 2)
```

### Drawing Polygons

- Pretty simple. Attributes are (screen, color, [[x1, y1],[x2, y2],[x3, y3]], thickness).

```python
# This draws a triangle using the polygon command
pygame.draw.polygon(screen, BLACK, [[100,100], [0,200], [200,200]], 5)
```

### Drawing Text

- There are three basic steps to drawing text:
  1. Setting the font
  2. Making a stamp
  3. Displaying the stamp
- Make the font outside the main loop.

```python
# Select the font to use, size, bold, italics
font = pygame.font.SysFont('C:\\Fonts\\Calibri', 25, True, False)

# Render the text. "True" means anti-aliased text.
# Black is the color. The variable BLACK was defined
# above as a list of [0, 0, 0]
# Note: This line creates an image of the letters,
# but does not put it on the screen yet.
text = font.render("My text",True,BLACK)

# Put the image of the text on the screen at 250x250
screen.blit(text, [250, 250])


# Use this code for string conversion
text = font.render("Score: " + str(score), True, BLACK)
```  
