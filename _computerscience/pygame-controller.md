---
title: "pygame Controllers and Graphics"
excerpt: "Learning to use pygame Animations"
date: 2020-07-06
toc: true
---


### Introduction

- So far, we've shown how to animate items on the screen, but not how to interact with them.
- To begin with, it is necessary to have an object that can be moved around the screen. The best way to do this is to have a function that takes in an x and y coordinate, then draws an object at that location.
- Let's take a look at how to write a function to draw an object.

```python
# Draw a Snowman
def draw_snowman(screen, x, y):
    # Draw a circle for the head
    pygame.draw.ellipse(screen, WHITE, [35 + x, y, 25, 25])
    # Draw the middle snowman circle
    pygame.draw.ellipse(screen, WHITE, [23 + x, 20 + y, 50, 50])
    # Draw the bottom snowman circle
    pygame.draw.ellipse(screen, WHITE, [x, 65 + y, 100, 100])

# Draw a Stick Figure
#NOTE: Find the smallest x and y values. Subtract from each x and y. Don't mess with the width and height.
# Head
pygame.draw.ellipse(screen, BLACK, [1+x,y,10,10], 0)

# Legs
pygame.draw.line(screen, BLACK ,[5+x,17+y], [10+x,27+y], 2)
pygame.draw.line(screen, BLACK, [5+x,17+y], [x,27+y], 2)

# Body
pygame.draw.line(screen, RED, [5+x,17+y], [5+x,7+y], 2)

# Arms
pygame.draw.line(screen, RED, [5+x,7+y], [9+x,17+y], 2)
pygame.draw.line(screen, RED, [5+x,7+y], [1+x,17+y], 2)
```

### Mouse

- To get the position of the mouse cursor on the screen, use: **pos = pygame.mouse.get_pos()**
-  So if we do a *print(pos)* we get **(x,y)**
- Getting the mouse should go in the “game logic” part of the main program loop. The function call should go in the “drawing” part of the main program loop.
```python
# Game logic
pos = pygame.mouse.get_pos()
x = pos[0]
y = pos[1]

# Drawing section
draw_stick_figure(screen, x, y)
```

- You can hide the mouse cursor by using the code above the main loop.

```python
# Hide the mouse cursor
pygame.mouse.set_visible(False)
```

### Keyboard

- We need to:
  - Create an initial x and y for our start position.
  - Set a “velocity” in pixels per frame when an arrow key is pressed down. (keydown)
  - Reset the velocity to zero when an arrow key is released. (keyup)
  - Adjust the x and y each frame depending on the velocity.
- To start with, set the location and speed before the main loop starts:

```python
# Speed in pixels per frame
x_speed = 0
y_speed = 0

# Current position
x_coord = 10
y_coord = 10
```

- Inside the main while loop of the program, we need to add some items to our event processing loop.
- A pygame.KEYDOWN event is generated when a key is pressed down. A pygame.KEYUP event is generated when the user lets up on a key.
- When the user presses a key, the speed vector is set to 3 or -3 pixels per frame. When the user lets up on a key the speed vector is reset back to zero.

```python
for event in pygame.event.get():
    if event.type == pygame.QUIT:
        done = True

    # User pressed down on a key
    elif event.type == pygame.KEYDOWN:
        # Figure out if it was an arrow key. If so
        # adjust speed.
        if event.key == pygame.K_LEFT:
            x_speed = -3
        elif event.key == pygame.K_RIGHT:
            x_speed = 3
        elif event.key == pygame.K_UP:
            y_speed = -3
        elif event.key == pygame.K_DOWN:
            y_speed = 3

    # User let up on a key
    elif event.type == pygame.KEYUP:
        # If it is an arrow key, reset vector back to zero
        if event.key == pygame.K_LEFT or event.key == pygame.K_RIGHT:
            x_speed = 0
        elif event.key == pygame.K_UP or event.key == pygame.K_DOWN:
            y_speed = 0

# Move the object according to the speed vector.
x_coord += x_speed
y_coord += y_speed

# Draw the stick figure
draw_stick_figure(screen, x_coord, y_coord)
```

- For a list of all key-codes, visit [this](https://www.pygame.org/docs/ref/key.html).

### Controller

- To begin, check to see if the computer has a joystick, and initialize it before use. This is done *once*.

```python
# Count the joysticks the computer has
joystick_count = pygame.joystick.get_count()
if joystick_count == 0:
    # No joysticks!
    print("Error, I didn't find any joysticks.")
else:
    # Use joystick #0 and initialize it
    my_joystick = pygame.joystick.Joystick(0)
    my_joystick.init()
```

- Inside the main program loop, the values of the joystick returns may be multiplied according to how far an object should move.

```python
# This goes in the main program loop!

# As long as there is a joystick
if joystick_count != 0:

    # This gets the position of the axis on the game controller
    # It returns a number between -1.0 and +1.0
    horiz_axis_pos = my_joystick.get_axis(0)
    vert_axis_pos = my_joystick.get_axis(1)

    # Move x according to the axis. We multiply by 10 to speed up the movement.
    # Convert to an integer because we can't draw at pixel 3.5, just 3 or 4.
    x_coord = x_coord + int(horiz_axis_pos * 10)
    y_coord = y_coord + int(vert_axis_pos * 10)

# Clear the screen
screen.fill(WHITE)

# Draw the item at the proper coordinates
draw_stick_figure(screen, x_coord, y_coord)
```
