---
title: "Python Classes"
excerpt: "The basics of the Python Classes"
date: 2020-07-09
---

- Objects have attributes, such as a person's name, height, and age. Objects also have methods. Methods define what an object can do, like run, jump, or sit.

### Defining a Simple Class

- **PUT THE ATTRIBUTES OF OBJECTS WITHIN THE INIT FUNCTION IF YOU WANT THE OBJECT TO HAVE IT**
- If you specifiy it outside, it is shared between the whole class.
- we can define classes representing a character in a game and addresses:

```python
class Character():
    """ This is a class that represents the main character in a game. """
    def __init__(self):
        """ This is a method that sets up the variables in the object. """
        self.name = "Link"
        self.sex = "Male"
        self.max_hit_points = 50
        self.current_hit_points = 50
        self.max_speed = 10
        self.armor_amount = 8



class Address():
    """ Hold all the fields for a mailing address. """
    def __init__(self):
        """ Set up the address fields. """
        self.name = ""
        self.line1 = ""
        self.line2 = ""
        self.city = ""
        self.state = ""
        self.zip = ""
```

- The **def __init__(self):** in a special function called a *constructor* that is run automatically when the class is created.
- The self. is kind of like the pronoun my. A class pointing to itself.
- We can create an instance of the address class like this:

```python
# Create an address
home_address = Address()

# Set the fields in the address
home_address.name = "John Smith"
home_address.line1 = "701 N. C Street"
home_address.line2 = "Carver Science Building"
home_address.city = "Indianola"
home_address.state = "IA"
home_address.zip = "50125"


# Editing the name value
# Alert! This does not set the address's name!
name = "Zain"

# This doesn't set the name for the address either
Address.name = "Zain"

# This does work:
my_address.name = "Zain"
```

### Functions in Classes

- Functions are defined basically the same with one important change: the paramater **self**.
- The first parameter of any method in a class must be self. This parameter is required even if the function does not use it.

```python
class Dog():
    def __init__(self):
        self.age = 0
        self.name = ""
        self.weight = 0

    def bark(self):
        print("Woof")
```

- Here are the important items to keep in mind when creating methods for classes:
  - Attributes should be listed first, methods after.
  - The first parameter of any method must be self.
  - Method definitions are indented exactly one tab stop.

- Methods may be called in a manner similar to referencing attributes from an object.
- Note that even through the bark function has one parameter, self, the call does not pass in anything. This is because the first parameter is assumed to be a reference to the dog object itself.
- The function can access the class's attributes by referencing self.

```python
my_dog = Dog()

my_dog.name = "Spot"
my_dog.weight = 20
my_dog.age = 3

my_dog.bark()
```


- Below is an example of a ball class.

```python
Class Ball():
    def __init__(self):
        # --- Class Attributes ---
        # Ball position
        self.x = 0
        self.y = 0

        # Ball's vector
        self.change_x = 0
        self.change_y = 0

        # Ball size
        self.size = 10

        # Ball color
        self.color = [255,255,255]

    # --- Class Methods ---
    def move(self):
        self.x += self.change_x
        self.y += self.change_y

    def draw(self, screen):
        pygame.draw.circle(screen, self.color, [self.x, self.y], self.size )
```

### References

- Look at the code below and see how Nancy is just a shallow copy of Bob. That's because these variables are just pointers. What happened is that Nancy is now pointing at the memory location of Bob.

```python
Class Person():
    def __init__(self):
        self.name = ""
        self.money = 0

bob = Person()
bob.name = "Bob"
bob.money = 100

nancy = bob
nancy.name = "Nancy"

print(bob.name, "has", bob.money, "dollars.")
print(nancy.name, "has", nancy.money, "dollars.")
```

- Bob and Nancy are **REFERENCES**. If you pass Bob to a function and try to edit it, it **DOES NOT** make a copy. It'll change the attributes of the object you sent.
- Arrays work the same way. A function that takes in an array (list) as a parameter and modifies values in that array will be modifying the same array that the calling code created. The address of the array is copied, not the entire array.

```python
def give_money2(person):
    person.money += 100

give_money2(bob)
print(bob.money)
```

### Constructors

- Oh boy, this one was tough. Python doesn't have different types of constructors but we can play around that.
- The default constructor is explained below.

```python
class Dog():
    def __init__(self):
        """ Constructor. Called when creating an object of this type. """
        self.name = ""
        print("A new dog is born!")

# This creates the dog
my_dog = Dog()
```

- However, if we want to copy an object (like the copy constructor), we can use the **copy** library.

```python
# For the Dog class above
import copy

# Shallow Copy
# This does create a new object but doesn't recursively create ALL new objects. The references inside are the same.
# Basically if you have objects within an object, it creates a new object for the outer object but keeps references of the inner ones.
my_dog = Dog()
new_dog = copy.copy(my_dog)

# Deep Copy
# This creates a COMPLETELY NEW OBJECT WITH ALL NEW OBJECTS INSIDE OF IT. No references. No hassle.
my_dog = Dog()
new_dog = copy.deepcopy(my_dog)
```

- If you want a paramerterized constructor, you have to do it yourself.

```python
class Cat():
    name = ""
    color = ""
    weight = 0
    # Main Constructor Calls

    def __init__(self, name=None, color=None, weight=None):
        if name is not None and color is not None and weight is not None:
            self.parameterized_constructor(name, color, weight)
        else:
            self.default_constructor()

    # Parameter Constructor
    def parameterized_constructor(self, name, color, weight):
        self.name = name
        self.color = color
        self.weight = weight
        self.cat_head = Head()
        print("Parameters set, Cat created.")

  # Default Constructor
    def default_constructor(self):
        print("Default Cat created.")
```


### Inheritance

- It is possible to create a class and inherit all of the attributes and methods of a parent class.
- An examples are listed below.

```python
#Parent Class
class Boat():
  def __init__(self):
      self.tonnage = 0
      self.name = ""
      self.is_docked = True

  def dock(self):
      if self.is_docked:
          print("You are already docked.")
      else:
          self.is_docked = True
          print("Docking")

  def undock(self):
      if not self.is_docked:
          print("You aren't docked.")
      else:
          self.is_docked = False
          print("Undocking")

#Submarine is the child class inheriting from Boat
class Submarine(Boat):
  def submerge(self):
    print("Submerge!")
```



### Overriding Functions

- The **super()** keyword allows you to call the parent function in a child class.
- If the child class has a function that has the same name as a function in the parent class, it automatically overrides the parent function. Only the child function is called.

```python
class Person():
    def __init__(self):
        self.name = ""

    def report(self):
        # Basic report
        print("Report for", self.name)

class Employee(Person):
    def __init__(self):
        # Call the parent/super class constructor first
        super().__init__()

        # Now set up our variables
        self.job_title = ""

    def report(self):
        # Here we override report and just do this:
        print("Employee report for", self.name)

class Customer(Person):
    def __init__(self):
        super().__init__()
        self.email = ""

    def report(self):
        # Run the parent report:
        super().report()
        # Now add our own stuff to the end so we do both
        print("Customer e-mail:", self.email)

john_smith = Person()
john_smith.name = "John Smith"

jane_employee = Employee()
jane_employee.name = "Jane Employee"
jane_employee.job_title = "Web Developer"

bob_customer = Customer()
bob_customer.name = "Bob Customer"
bob_customer.email = "send_me@spam.com"

john_smith.report()
jane_employee.report()
bob_customer.report()
```

### Is-A and Has-A Relationship

- A parent class should always be a more general, abstract version of the child class. This type of child to parent relationship is called an is a relationship. or example, a parent class Animal could have a child class Dog.
- A person could have a dog, and that would be implemented by having the Person class have an attribute for Dog. The Person class would not derive from Dog because that would be some kind of insult.

### Static Variables vs. Instance Variables

- An **instance variable** is the type of class variable we've used so far. Each instance of the class gets its own value. For example, in a room full of people each person will have their own age. Some of the ages may be the same, but we still need to track each age individually.
- With **static variables** the value is the same for every single instance of the class. Even if there are no instances, there still is a value for a static variable.

```python
# Example of an instance variable
class ClassA():
    def __init__(self):
        self.y = 3

# Example of a static variable
class ClassB():
    x = 7

# Create class instances
a = ClassA()
b = ClassB()

# Two ways to print the static variable.
# The second way is the proper way to do it.
print(b.x)
print(ClassB.x)

# One way to print an instance variable.
# The second generates an error, because we don't know what instance
# to reference.
print(a.y)
print(ClassA.y)
```
