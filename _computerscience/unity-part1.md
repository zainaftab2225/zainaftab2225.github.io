---
title: "Unity3D - Part 1"
excerpt: "The very basics of Unity3D"
date: 2020-07-20
---

### Introduction

 - Unity is a cross-platform game engine that uses C# code for its scripts.

### Setting up the Environment

#### 1. Download Visual Studio

1. Download Visual Studio Community 2019 at this [link](http://www.visualstudio.com/).
2. Run the install file you downloaded.
3. In the workloads area, select **Windows: .NET desktop development** and **Mobile & Gaming: Game development with Unity**.
4. Continue and finish installation.

#### 2. Download Unity Hub

1. Download Unity Hub at this [link]( http://unity.com/).
2. Run the install file you downloaded.
3. Continue and finish installation with default values.
3. Start Unity Hub, go to installs download the latest version of Unity. Make sure there is an **f** in the version number as this indicates long-term support. Unity Hub lets you have many different versions of Unity.
4. In Unity Hub, click Projects and create a new 2D project.
5. After some time, the Unity editor will open. Change the layout to **2 by 3** layout. It is a very intuitive layout.
6. Save the layout for future projects.

### First Unity Script

- Below is a simple C# script that prints a message on the Unity console window. Note that we use **print** and not **Console.Writeline()**.
- The **Start** method is called before the first frame update. It is only called when the script that is attached to the object is enabled. It is only called once in the object's lifetime.
- There is another method called the **Awake** method which is called even before the Start method. It is called even if the script is disabled. It is also only called once in the object's lifetime.
- **MonoBehaviour** is a Unity Class that we inherit from.


```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

/// <summary>
/// Prints a message
/// </summary>
public class PrintMessage : MonoBehaviour
{
	/// <summary>
	/// Use this for initialization
	/// </summary>
	void Start()
	{
		// print supportive message
        print("Hi, n00b!");
	}
}
```


### Data Types

 - We can represent **N** amount of numbers if we have **b** number of bits using the formula: **N=2^b**
 - So for example, if we have 2 bits, we can encode 4 things as 2^2=4.
 - In C#, we have many different numeric data types. The main ones are: **int**,  **float**, **long** and **double**.
 - Click [here](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/integral-numeric-types) to read more about them in detail.



### Floats

 - It's actually impossible for us to represent the whole range of infinite real numbers in a computer.
 - To represent decimals, we use float. However if we declare a decimal in C# without implicitly stating it is a float, the compiler considers it to be double. Therefore, we need to declare a float like this: **float myVar = 0.25f**
 - The compiler gives an error if you don't add the *f* because you are trying to insert a double value (8 bytes) into a float variable (4 bytes).

### Type-casting

 - You can explicitly type-cast for a certain operation by adding the datatype in brackets before the variable. It is shown in code below.


 ```cs
 ...
 float deltaX = point2X - point1X;
 float deltaY = point2Y - point1Y;

 //Explicit Type-Casting

 float distanceBetweenPoints = (float)Math.Sqrt(Math.Pow((double)deltaY, 2) + (Math.Pow((double)deltaX, 2)));
 ```


### Variables, Constants and Properties

 - Variable declaration is simple e.g. **int myVar**.
 - Constants don't change. You can declare a constant by doing: **const int myConstant**.
 - Properties are fun. They are basically getter-setters which hide the actual fields in a class by using **private** access modifier. Whatever the **value** user gives, it is assigned to the field inside the property. In the consumer code, you can just access it like a variable. An example is given below:

 ```cs
 private int age;

 public int Age
 {
   get
   {
     return age;
   }
   set
   {
     age = value;
   }
 }
 ```
