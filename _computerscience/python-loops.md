---
title: "Looping in Python"
excerpt: "The basics of for and while loops"
date: 2020-07-02
---

There are two major types of loops in Python, **for** loops and **while** loops.

### For Loops

- The for loop example below runs the print statement five times.
- Indentation rule is the same as if statements.
- The range function controls how many times the code in the loop is run.

```python
for i in range(5):
    print("I must not tell lies.")
```

- You can use the range function in many different ways to control the loop. Some examples are given below.

```python

# Printing 0-9 on screen
for i in range(10):
    print(i)

# Printing 1-10 on screen
for i in range(1, 11):
    print(i)

# Increments in range

# Two ways to print the even numbers 2 to 10
for i in range(2,12,2):
    print(i)

for i in range(5):
    print((i + 1) * 2)        


```

#### Nesting For Loops

- Indent to nest loops. Example is given below.

```python
for i in range(3):
    print("a")
    for j in range(3):
        print("b")

print("Done")
```

#### Keeping a Running Total

- A common operation in working with loops is to keep a running total.

```python
total = 0
for i in range(5):
    new_number = int(input("Enter a number: " ))
    total += new_number
print("The total is: ", total)
```

### While Loops

-  A while loop is used when a program needs to loop until a particular condition occurs.
- The range function only works with the for loop. Do not use it with the while loop!

```python
# Printing 0 to 9
i = 0
while i < 10:
    print(i)
    i = i + 1


```

#### Increments in Python

- **i = i + 1** and **i += 1** are the same.
- Also can be used for subtraction and multiplication e.g. **'-='**

### Random Numbers

- To use random numbers, the first thing that should appear at the top of the program is an import statement: **import random**
- It is important not to create a file with the same name as what is being imported. Creating a file called **random.py** will cause Python to start importing that file instead of the system library that creates random numbers.
- Random numbers can be created using the **randrange** function.

```python

# Random number from 0 to 10
my_number = random.randrange(11)

# Random number from 100 to 200
my_number = random.randrange(100, 201)

# Picking a random item out of a list
my_list = ["Ellie", "Abby", "Fat Geralt"]
random_index = random.randrange(3)
print(my_list[random_index])
```

- If you want a random floating point number, use the **random** function. An example is given below:

```python

# Random floating point number from 0 to 1
my_number = random.random()

# Random floating point number between 10 and 15
my_number = random.random() * 5 + 10
```
