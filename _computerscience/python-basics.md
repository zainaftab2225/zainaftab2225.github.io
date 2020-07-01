---
title: "Python Basics"
excerpt: "The basics of the language syntax"
date: 2020-07-01
---

### Printing

- Output any expression to the screen using the **print()** function.
- To print a blank line  use the following code: **print()**

```python
print("Hello World") # Hello World
print("The answer of 2+2 is: ", 2+2) # The answer of 2+2 is: 4
print("The answer of 2+2 is: ", "2+2") # The answer is: 2+2
```

- To output double quotes within the text, use **\"**. This is called an *escape code*.

```python

print("Hello \" World ") # Hello " World

```

- Some other important escape codes are listed in the table below.

| Escape Code | Description |
|------- | ---------|
| \' | Single Quote |
| \" | Double Quote |
| \t | Tab |
| \r | Carriage Return |
| \n | Linefeed/New Line |

### Comments

- Comments can be added by using the # symbol at the beginning of a line.
- A codeblock can also be commented by adding ''' three single quotes.

```python
print("Hi")
'''
This is
a
multi
line
comment. Nothing
Will run in between these quotes.
print("There")
'''
print("Done")
```

### Assignment Operators

- Same basic rule as other languages: the right hand side is assigned to the left hand side.
- There are assignment operations for addition, subtraction, multiplication and division.

```python
# Create a variable x
# Store the value 10 into it.
x = 10

# This prints the value stored in x.
print(x)

# This prints the letter x, but not the value in x
print("x")

# This prints "x= 10"
print("x=", 10)
```

### Variables

- Variables should start with a lower case letter.
- Variables can start with an upper case letter or an underscore, but those are special cases and should not be done on a normal basis.
- Variables are case sensitive as in the example below. X and x are two different variables.

```python
x = 6
X = 5
print(x)
```

- The official style guide for Python says that multi-word variable names in Python should be separated by underscores. But do I care? Both **my_variable** and **myVariable** works.
- Constant variables can have an upper-case name e.g. **MAX_SPEED**, **MAX_SCORE**, etc.

### Operators

- Some operators are listed in the table below for reminders.
- The official style guide for Python says that there should be a space before and after each operator.

| Operator | Operation | Example Equation | Example Code | Output |
|------- | ---------| ---------| ---------| ---------|
| + | addition | 3+2 | a = 3 + 2 | 5 |
| - | subtraction	| 3-2 |	a = 3 - 2 | 1 |
| * | multiplication	| 3x2 | 	a = 3 * 2 | 6 |
| / | division | 10/2 |	a = 10 / 2 | 5 |
| // | floor division	| N/A |	a = 10 // 3 | 3 |
| ** | power	| 2^3 | 	a = 2 ** 3 | 8 |
| % | modulus | 	N/A |	a = 8 % 3 | 2 |

### Trigonometric Functions

- Math library is available for trigonometric functions: **math**. Example to import everything from math is given below.
- Units are in radians.

```python
# Import the math library
# This line is done only once, and at the very top
# of the program.
from math import *

(10)
x = sin(0) + cos(0)
```
### Input

- Input in Python is text only; need to be converted to other data types.

```python
number = input("Enter your number: ")
number = float(number)

# Can be done in one step
number2 = float(input("Enter your second number: "))
```

### If Statements

- The if statement allows a computer to make a decision.
- Indentation *matters* a lot here. If blocks use indentation to know whether to execute or not.
- An if statement can check multiple conditions by chaining together comparisons with **and** and **or**.

```python

# Variables used in the example if statements
a = 4
b = 5

# Basic comparisons
if a < b:
    print("a is less than b")

if a > b:
    print("a is greater than b")

print("Done")

# Indentation must be the same, this does NOT work
if a == 1:
  print("Indented two spaces.")
    print("Indented four. This will generate an error.")
   print("The computer will want you to make up your mind.")
```

| Conditional Operator | Description |
|------- | ---------|
| < | Less Than |
| > | Greater Than |
| <= | Lesser Than or Equal |
| >= | Greater Than or Equal |
| == | Equal |
| != | Not Equal |
| and | AND Operator |
| or | OR Operator |
| not | NOT Operator |



### Boolean Variables

- Boolean variables are: **True** and **False**.

```python
# Boolean data type. This is legal!
a = True
if a:
    print("a is true")
```

- The **not** operator flips the value. So if a is *true*, you can make it false by using 'not a'.

```python

# Using not
a = True
b = not a # Value in b is 'False'

# How to use the not function
if not(a):
    print("a is false")

# Can also be used like this, looks better - use this
if not a:
    print("a is false")    
```

- You can compare and assign at the same time. Check the code block below.

```python
a = 3
b = 3
# This next line is strange-looking, but allowed.
# c will be true or false, depending if
# a and b are equal.
c = a == b
# Prints value of c, in this case True
print(c)
```

- If you do 'if 0', then it is treated as false. It won't run. Any value other than 0 will be true.

```python

# Nothing will be printed
if 0:
    print("Zero")

# Will print
if 1:
    print("1")
if "A":
    print("A")
```

- Another weird example is given below. *b* is always true in the first if statement so it'll print no matter what.


```python
a = "c"
if a == "B" or "b":
    print("a is equal to b. Maybe.")

# This is the way to do the if statement for comparison with a
if a == "B" or a == "b":
    print("a is equal to b.")
```    

### Else and Else If

- **Else** is just else:
- **Else If** is elif *<statement>*:
- **REMINDER**: Order of execution matters.

```python

temperature = int(input("What is the temperature in Fahrenheit? "))
if temperature > 90:
    print("It is hot outside")
elif temperature < 30:
    print("It is cold outside")
else:
    print("It is not hot outside")
print("Done")

```

### Text Comparisons

- It is possible to use an if statement to check text.

```python

user_name = input("What is your name? ")
if user_name == "Zain":
    print("You have a nice name.")
else:
    print("Your name is ok.")

```

- If the program needs to match regardless as to the case of the text entered, the easiest way to do that is to convert everything to lower case. This can be done with the **lower** command.

```python
user_name = input("What is your name? ")
if user_name.lower() == "zain":
    print("You have a nice name.")
else:
    print("Your name is ok.")
```    
