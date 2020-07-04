---
title: "Lists in Python"
excerpt: "Basics of Lists in Python"
date: 2020-07-04
---

### Data Types

- Python can display what type of data a value is with the type function.

```python
type(3) # <class 'int'>
type(3.145) # <class 'float'>
type("Hi there") # <class 'str'>
type(True) # <class 'bool'>
type(  (2, 3, 4, 5) ) # <class 'tuple'>
type(  [2, 3, 4, 5] ) # <class 'list'
```

### Working with Lists

- Lists are similar to another data structure called an array. A list can be resized, but an array can not.
- Also, a program can create a “tuple.” This data type works just like a list, but with two differences. First, it is created with parentheses rather than square brackets. Second, it is not possible to change the tuple once created.

```python
x = [1,2,3,4,5]
for i in x:
  print(i)
```

### Iterating through a List

- Two types of for loops that can do this:
  1. **For-each** where the format is for *item_variable* in *list_name*
  2. **Index** where the format is for *index* in range(len(*list_name*))
- Examples are shown below.

```python

# Method 1
my_list = [101, 20, 10, 50, 60]
for item in my_list:
    print(item)

# Method 2

my_list = [101, 20, 10, 50, 60]
for i in range(len(my_list)):
    print(my_list[i])
```

### Adding to a List

- New items may be added to a list (but not a tuple) by using the append command.

```python
my_list = [2, 4, 5, 6]
print(my_list) # [2,4,5,6]
my_list.append(9)
print(my_list) # [2,4,5,6,9]
```

- To create a list from scratch, it is necessary to create a blank list and then use the append function. This example creates a list based upon user input:

```python
# Creating a list of numbers from user input
my_list = [] # Empty list
for i in range(5):
    user_input = input( "Enter an integer: ")
    user_input = int(user_input)
    my_list.append(user_input)
    print(my_list)
```

- If a program needs to create an array of a specific length, all with the same value, a simple trick is to use the following code:

```python
# Create an array with 100 zeros.
my_list = [0] * 100
```

### Summing or Modifying a List

- You can modify the element of a list by using: *list_name*[index] = *new_value*

```python
# Doubling the values of an array
# Copy of the array to modify
my_list = [5, 76, 8, 5, 3, 3, 56, 5, 23]

# Loop from 0 up to the number of elements
# in the array:
for i in range(len(my_list)):
    # Modify the element by doubling it
    my_list[i] = my_list[i] * 2

# Print the result
print(my_list)
```

### Slicing Strings

- A string in Python is just a list. So if you have x = "Hello my name is Zain", you can access the *Z* character using **x[17]**.
- You can access the last character in Python in a list by doing x[-1].
- You can get the length of a string by using the **len** function: *print(len(x))*
- You can access substrings using the colon: x[0:4] will be 'Hell' in the above example.
  - Can also be x[:6] (this just means 0-6).
  - Can also be x[6:] (starting at 6 and going to the end).
  - Can also be x[6:10] (starting at 6, going upto 10 but not including 10).
- You can also do arithmetic with strings:
  - print (a+b) is **concatenation of a and b**.
  - print (a*2) is printing the string *a* twice.
  
```python
x = "This is a sample string"
#x = "0123456789"

print("x=", x)

# Accessing a single character
print("x[0]=", x[0])
print("x[1]=", x[1])

# Accessing from the right side
print("x[-1]=", x[-1])

# Access 0-5
print("x[:6]=", x[:6])
# Access 6
print("x[6:]=", x[6:])
# Access 6-8
print("x[6:9]=", x[6:9])

#Arithmetic
a = "Hi"
b = "There"
c = "!"
print(a + b)
print(a + b + c)
print(3 * a)
print(a * 3)
print((a * 2) + (b * 2)) #HiHiThereThere

for character in "This is a test.":
    print(character)
```  
### Secret Codes

- To get ASCII of a character, use: **ord("A")**
- To convert to a character from ASCII, use: **chr(65)** which gets you A

### Associative Arrays

- Python is not limited to using numbers as an array index. It is also possible to use an associative array. An associative array works like this.

```python
# Create an empty associative array
# (Note the curly braces.)
x = {}

# Add some stuff to it
x["fred"] = 2
x["scooby"] = 8
x["wilma"] = 1

# Fetch and print an item
print(x["fred"])
```
