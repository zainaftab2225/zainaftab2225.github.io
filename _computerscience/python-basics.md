---
title: "Python Basics"
date: 2020-06-30
---

### Printing

- Output any expression to the screen using the **print()** function.

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

| Operator | Operation | Example Equation | Example Code | Output |
|------- | ---------| ---------| ---------| ---------|
| + | addition | 3+2 | a = 3 + 2 | 5 |
| - | subtraction	| 3-2 |	a = 3 - 2 | 1 |
| * | multiplication	| 3x2 | 	a = 3 * 2 | 6 |
| / | division | 10/2 |	a = 10 / 2 | 5 |
| // | floor division	| N/A |	a = 10 // 3 | 3 |
| ** | power	| 2^3 | 	a = 2 ** 3 | 8 |
| % | modulus | 	N/A |	a = 8 % 3 | 2 |
