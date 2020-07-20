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
3. In the workloads area, select *Windows: .NET desktop development* and *Mobile & Gaming: Game development with Unity*.
4. Continue and finish installation.

### 2. Download Unity Hub

1. Download Unity Hub at this [link]( http://unity.com/).
2. Run the install file you downloaded.
3. Continue and finish installation with default values.
3. Start Unity Hub, go to installs download the latest version of Unity. Make sure there is an *f* in the version number as this indicates long-term support. Unity Hub lets you have many different versions of Unity.
4. In Unity Hub, click Projects and create a new 2D project.
5. After some time, the Unity editor will open. Change the layout to *2 by 3* layout. It is a very intuitive layout.
6. Save the layout for future projects.

### First Unity Script

- Below is a simple C# script that prints a message on the Unity console window. Note that we use *print* and not *Console.Writeline()*.
- The *Start* method is called before the first frame update. It is only called when the script that is attached to the object is enabled. It is only called once in the object's lifetime.
- There is another method called the *Awake* method which is called even before the Start method. It is called even if the script is disabled. It is also only called once in the object's lifetime.


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

### Floats
