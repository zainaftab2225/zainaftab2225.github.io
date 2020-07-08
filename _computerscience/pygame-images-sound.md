---
title: "pygame Images and Sound"
excerpt: "Adding Images and Sound"
date: 2020-07-08
---

### Images

- To set up an image, we need to load it in a variable and then blit it to the screen.

```python
# Image should be loaded once before the main loop
bg_image = pygame.image.load("saturn_family1.jpg").convert()

# Blit within main loop. 0,0 specifies where to start image on screen.
screen.blit(background_image, [0, 0])
```

- You can control the image if you take the coordinates from the user.

```python
# Get the current mouse position. This returns the position
# as a list of two numbers.
player_position = pygame.mouse.get_pos()
x = player_position[0]
y = player_position[1]

# Copy image to screen:
screen.blit(player_image, [x, y])
```

- Use the **convert()** function while loading or **convert_alpha()** if there is some transparency in the image.
- If you want to make a color transparent, see this as as example: **player_image.set_colorkey(BLACK)**

### Sound

The following command loads a sound file and creates a variable named click_sound to reference it:

```python
click_sound = pygame.mixer.Sound("laser5.ogg")

#We can play the sound by using the following command:
click_sound.play()


# If user clicks then play
for event in pygame.event.get():
    if event.type == pygame.QUIT:
        done = True
    elif event.type == pygame.MOUSEBUTTONDOWN:
        click_sound.play()
```
