---
title: "pygame Animations"
excerpt: "Learning to use pygame Animations"
date: 2020-07-06
toc: false
---
- Within the loop of 60 frames, you can make variables and move the coordinates. When new coordinates are set and a newer frame is displayed, it gives the illusion to the user that there is an animation.
- Below is an example of how to create a bouncing rectangle.

```python
# Starting position of the rectangle
rect_x = 50
rect_y = 50

# Speed and direction of rectangle
rect_change_x = 5
rect_change_y = 5

# -------- Main Program Loop -----------
while done == False:
    for event in pygame.event.get(): # User did something
        if event.type == pygame.QUIT: # If user clicked close
            done = True # Flag that we are done so we exit this loop

    # Change the location of the rectangle each frame
    rect_x += rect_change_x
    rect_y += rect_change_y

    # If you hit the wall, redirect
    if rect_y > 450 or rect_y < 0:
          rect_change_y = rect_change_y * -1
    if rect_x > 650 or rect_x < 0:
          rect_change_x = rect_change_x * -1
    # Set the screen background
    screen.fill(BLACK)

    # Draw the rectangle
    pygame.draw.rect(screen, WHITE, [rect_x, rect_y, 50, 50])

```
- Neat code for animating snow also given below.

```python
# Import a library of functions called 'pygame'
import pygame
import random

# Initialize the game engine
pygame.init()

BLACK = [0, 0, 0]
WHITE = [255, 255, 255]

# Set the height and width of the screen
SIZE = [400, 400]

screen = pygame.display.set_mode(SIZE)
pygame.display.set_caption("Snow Animation")

# Create an empty array
snow_list = []

# Loop 50 times and add a snow flake in a random x,y position
for i in range(50):
    x = random.randrange(0, 400)
    y = random.randrange(0, 400)
    snow_list.append([x, y])

clock = pygame.time.Clock()

# Loop until the user clicks the close button.
done = False
while not done:

    for event in pygame.event.get():   # User did something
        if event.type == pygame.QUIT:  # If user clicked close
            done = True   # Flag that we are done so we exit this loop

    # Set the screen background
    screen.fill(BLACK)

    # Process each snow flake in the list
    for i in range(len(snow_list)):

        # Draw the snow flake
        pygame.draw.circle(screen, WHITE, snow_list[i], 2)

        # Move the snow flake down one pixel
        snow_list[i][1] += 1

        # If the snow flake has moved off the bottom of the screen
        if snow_list[i][1] > 400:
            # Reset it just above the top
            y = random.randrange(-50, -10)
            snow_list[i][1] = y
            # Give it a new x position
            x = random.randrange(0, 400)
            snow_list[i][0] = x

    # Go ahead and update the screen with what we've drawn.
    pygame.display.flip()
    clock.tick(20)

# Be IDLE friendly. If you forget this line, the program will 'hang'
# on exit.
pygame.quit()
```
