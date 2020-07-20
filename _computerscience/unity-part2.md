---
title: "Unity3D - Part 2"
excerpt: "Basics of Classes and Objects in Unity3D"
date: 2020-07-20
---



### Unity Scenes and Game Objects

- Unity has scenes which is what to show to the player.
Every scene consists of game objects which can range from the main camera to the player sprite to the environment. Everything within a scene is a game object.

### Classes and Objects in Unity

- As a general rule, the scripts that we write in Unity are classes.
- When we attach a script as a component to a game object in a Unity scene, then we get an instance of the class, specifically an object attached to that game object.


### Fields

- Attributes of an object are called fields.
- They can be primitive data types such as **int** or they can be **objects** as well.

### Methods

- A method is a block of code which only runs when it is called.
- You can pass data, known as parameters, into a method.
- You can return some value from a method as well.

```cs
class Program
{
  static void MyMethod()
  {
    // code to be executed
  }
}
```

### Constructor

- A constructor is a special method that is used to initialize objects. The advantage of a constructor, is that it is called when an object of a class is created. It can be used to set initial values for fields.

```cs
// Create a Car class
class Car
{
  public string model;  // Create a field

  // Create a class constructor for the Car class
  public Car()
  {
    model = "Mustang"; // Set the initial value for model
  }

  // Create a class constructor with a parameter
  public Car(string modelName)
  {
    model = modelName;
  }

  static void Main(string[] args)
  {
    Car Ford = new Car();  // Create an object of the Car Class (this will call the constructor)
    Console.WriteLine(Ford.model);  // Print the value of model
  }
}
// Outputs "Mustang"
```
