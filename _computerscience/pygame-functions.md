---
title: "Python Functions"
excerpt: "The basics of the Python Functions"
date: 2020-07-07
---


### def

- By defining a function we can make the program easier to read. To define a function, start by using the **def** command.
- Following the function name will be a set of parentheses and a colon. All the commands for the function will be indented inside. See the example below.

```python
def draw_tree():
    pygame.draw.rect(screen, BROWN, [60, 400, 30, 45])
    pygame.draw.polygon(screen, GREEN, [[150, 400], [75, 250], [0, 400]])
    pygame.draw.polygon(screen, GREEN, [[140, 350], [75, 230], [10, 350]])
```

### Calling a Function

- You have to call the function to actually run the code in the function and get the tree to draw.

```python
draw_tree()
draw_house()
draw_car()
draw_killer_bunny()
```

### Paramters

- Adjusting the functions to add parameters, examples below.

```python

# Drawing a tree with passing values
def draw_tree(screen, x, y):
    pygame.draw.rect(screen, BROWN, [60+x, 170+y, 30, 45])
    pygame.draw.polygon(screen, GREEN, [[150+x,170+y],[75+x,20+y], [x,170+y]])
    pygame.draw.polygon(screen, GREEN, [[140+x,120+y], [75+x,y], [10+x,120+y]])


# Calculating Volume
def volume_sphere(radius):
    pi = 3.141592653589
    volume = (4 / 3) * pi * radius ** 3
    print("The volume is", volume)
```

### Returning and Capturing Values

- Just use the return statement, example is below.

```python
# Add two numbers and return the results
def sum_two_numbers(a, b):
    result = a + b
    return result
```

- We need to capture the result. We do that by setting a variable equal to the value the function returned.

```python
# Store the function's result into a variable
my_result = sum_two_numbers(22, 15)
print(my_result)
```

### Documenting Functions

- Functions in Python typically have a comment as the first statement of the function. This comment is delimited using three double quotes, and is called a **docstring**.
- The great thing about using docstrings in functions is that the comment can be pulled out and put into a website documenting your code using a tool like Sphinx.

```python
def volume_cylinder(radius, height):
    """Returns volume of a cylinder given radius, height."""
    pi = 3.141592653589
    volume = pi * radius ** 2 * height
    return volume
```

### Scope

- The use of functions introduces the concept of scope. Scope is where in the code a variable is “alive” and can be accessed. For example, look at the code below.

```python
# Define a simple function that sets
# x equal to 22
def f():
    x = 22

# Call the function
f()
# This fails, x only exists in f()
print(x)
```

- In the following code, x is created before the f() function, and thus can be read from inside the f() function.

```python
# Create the x variable and set to 44
x = 44

# Define a simple function that prints x
def f():
    print(x)

# Call the function
f()
```

- But you can't do this.

```python
# Create the x variable and set to 44
x = 44

# Define a simple function that prints x
def f():
    x += 1
    print(x)

# Call the function
f()
```

- You can use *global* before variable name in function to let the function know to reference the global variable.

### Pass-by-copy

- It gets confusing is if both the code that calls the function and the function itself have variables named the same. However, they are two different variables with two different memory locations.

```python
# Define a simple function that prints x
def f(x):
    x += 1
    print(x)

# Set x
x = 10
# Call the function
f(x)
# Print x to see if it changed
print(x)
```

### Functions Calling Functions

- It is entirely possible for a function to call another function. For example, say the functions like the following were defined:

```python
def arm_out(whichArm, palmUpOrDown):
    # code would go here

def hand_grab(hand, arm):
    # code goes here

def macarena():
    arm_out("right", "down")
    arm_out("left", "down")
    arm_out("right", "up")
    arm_out("left", "up")
    hand_grab("right", "left arm")
    hand_grab("left", "right arm")
    # etc
```

### Global Variables and Main Function

- Variables created at “indent level 0” are called **global variables**.
- Global variables are a very bad thing. Why? Because any piece of code anywhere can change their value. If you have a 50,000 line program, each line of code can change that global variable. If instead you keep the variable in a function, then only that code in the function can change the variable.
- A better way to write a program in Python would be to follow the pattern below. In this case all the code that I normally would have run at indent level 0 is placed in the main function. The last line of the file calls main.

```python
def main():
    print("Hello world.")

main()
```

- But there's a problem. If we used the import command on this module, it would automatically start running the main function. We don't want that. We want the program that imports it to control when the function is called.
- To fix this problem we can have our program check a global variable defined automatically by Python. We can check it to see if this code is being imported or run. If the code is being run, Python will automatically set the value of that variable to __main__. By using an if statement we will only call the main function if the code is being run.
- This is how all your Python code should be run:

```python
Proper use of a main function
def main():
    print("Hello world.")

if __name__ == "__main__":
    main()
```

If your script is being imported into another module, its various function and class definitions will be imported and its top-level code will be executed, but the code in the then-body of the if clause above won't get run as the condition is not met. As a basic example, consider the following two scripts:

- Script 1

```python
# file one.py
def func():
    print("func() in one.py")

print("top-level in one.py")

if __name__ == "__main__":
    print("one.py is being run directly")
else:
    print("one.py is being imported into another module")
```

- Script 2

```python
# file two.py
import one

print("top-level in two.py")
one.func()

if __name__ == "__main__":
    print("two.py is being run directly")
else:
    print("two.py is being imported into another module")
```

- If you run **python one.py**, output will be:

```python
# top-level in one.py
# one.py is being run directly
```

- If you run **python two.py**, output will be:

```python
# top-level in one.py
# one.py is being imported into another module
# top-level in two.py
# func() in one.py
# two.py is being run directly
```
