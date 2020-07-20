---
title: "Unity3D - Part 3"
excerpt: "Unity Editor, Debugger, Components and Update Function"
date: 2020-07-20
---

### Unity Editor

- The **Project** window holds everything that you put or might want to put in your game.
- The **Hierarchy** window contains everything in the current scene. By default, we get a main camera in our scene.
- The **Scene** window shows everything on the current scene.
- The **Game** window is what the player sees.
- The **Console** is used for debugging.
- The **Inspector** on the right shows the details about every game object that we select. We can modify the characteristics of the game object through the Inspector.

### Update Method

- The Update method is called every frame of the game object.

### Sprites and Game Objects

- Sprites are graphical assets that we include in our game.  A sprite can be a single image, or a single frame, if you will. Or it can be a set of frames that we could use for an animation for something in our game.
-  An important lesson is you should know before you have all of your art done, you should know what your standard sizes are going to be for that art, so that you can make sure your artist gives you the art that's the appropriate size. Also keep them in powers of 2.
- The Inspector can be used to **transform** the image. The size can be changed, the position can be changed, etc.
- The class we use to represent object's location and size is called **Vector3**. That's because it is an x, y and z coordinate. We can also use **Vector2** for the 2D plain for just x and y.

```cs
//Changing Size to four times the size of the Sprite
//Changing Position of object
public class Resizer : MonoBehaviour
{
    // Update is called once per frame
    void Update()
    {
      //For Size
      Vector3 newScale = transform.localScale;
      newScale.x = newScale.x*4;
      newScale.y = newScale.y*4;
      transform.localScale = newScale;

      //For Position (x,y,z)
      Vector3 newPosition = new Vector3(3, 2, 0);
      transform.position = newPosition;
    }
}
```

- Game objects are the entities that are actually in our game. So we add game objects to a scene in Unity, and then that game object is a thing that behaves within the context of the game world.



### Unity Component System

- The big idea here is that we can attach components to game objects in our scene, to affect both their state and their behavior.
- You can also modify the behavior of a particular game object by adding one or more scripts to it.
- So if we create and attach a script a game object, it will perform that functionality. An example is given below where our object will print something on the console window in Unity.

```cs
public class Talker : MonoBehaviour
{
  void Start()
  {
    print("Hello, I am speaking.");
  }
}
```

### Debugging in Unity

1. Add a breakpoint to your script in Vistual Studio.
2. Click **Attach to Unity** button at top.
3. Go back to Unity Editor and click play.
4. Your script will stop on your breakpoint.
5. Press F10 to move forward. Press F11 to jump into a function.

### 2D Physics

- We can attach the **RigidBody2D** component to our objects so that physics work on them.
- Another thing we can attach is a collider. There are many different types of colliders like Polygon Collider, Edge Collider, Box Collider, etc.
- We can create a script to make objects move as well. An example is given below.

```cs
public class Mover : MonoBehaviour
{
	/// <summary>
	/// Use this for initialization
	/// </summary>
	void Start()
	{
        // get the game object moving
        GetComponent<Rigidbody2D>().AddForce( new Vector2(0, 5), ForceMode2D.Impulse);		
	}
}
```

### Colliders and Physics Materials

- We can create materials and attach them to our game objects to alter their behavior. For example, we can attach a Physics material to tell the engine how much friction should act on the object or how bouncy the object is. We can also create materials to tell the engine how something should be rendered, etc.
- Below is a script which adds a random force on alien sprites, and prints ouch whenever they collide. The gravity of the project is set to 0 and the bounciness of the aliens are set to 2 by adding a Physics material. RigidBody2D and PolygonCollider2D are added to all aliens.

```cs
public class AlienCollider : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        float minForce = 2f;
        float maxForce = 5f;
        float angle = UnityEngine.Random.Range(0, (float)(2 * Math.PI));
        float magnitude = UnityEngine.Random.Range(minForce, maxForce);
        Vector3 direction = new Vector3((float)Math.Cos(angle), (float)Math.Sin(angle));
        GetComponent<Rigidbody2D>().AddForce(direction * magnitude, ForceMode2D.Impulse);
    }

    private void OnCollisionEnter2D(Collision2D collision)
    {
        print("OUCH!");
    }
}
```

### Prefabs

- Prefabs are prefabricated objects.
- If we want to make multiple game objects, we can just make a prefab and keep pasting that prefab.
