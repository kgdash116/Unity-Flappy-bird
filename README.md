# Unity-Flappy-bird
A repository for a flappy bird game made in Unity.

## Notes:

The Unity layout is split into 4 panels:
- Hierarchy
- Scene
- Inspector
- Project


GameObject: is an empty container, it has position and space, rotation and a scale. We can add components to it. The camera, bird, the pipes, the UI are all Game objects.
We use the inspector to manipulate our gameobjects.

We add physics , so our object ais effected by gravity (Rigidbody 2D) and a Circlecolider 2D for interaction with different objects.
By manipulating the circolider size in scene view we can get pass by the collision from the pillars.

## C# scripts:

- Start: All the code that is in Start is executed as soon as the script is enabled. It reuns precisely once.
- update: runs constantly , and will run every line of code every single frame over and over again.

Initially a gameobject script can only talk to its top bit and the transform. FOr this we need to make a special slot for RigidBody 2D in the script. Then wed be able to talk to it like change velocity etc. Once we have added a rigidbody object in our script we can drag and drop the rigibody 2D component fromt eh inspector into our script's rigidbody 2d slot. 

Variables when added tot he script can be manipulated from the inspector e.g flapstrength.

## Pipes:

- spawn in the game and are deleted when moved out of the view. well be making two pipes. Top pipe is a child of the parent component pipe and the bottom pipe is same as the top pipe but inverted.
- time.deltatime ensures that multiplication is always the same no matter the framerate. We didnt need this component in physics because it has its own clock.

- Prefabricated Gameobject: is made when we drag and drp[ opur parent pipe component. in our example pipes are made a prefab,
- The PipeSpawnScript spawns the new version of the pipe prefab every few seconds.

Attributes such as Health, time,score is also a game object.

Well use UnityEngine.UI for the player score.

well reference the Text object in the logic script.

For testing purposes inside the logic script we use [ContextMenu("Increase Score")], this will help us to increase the score manually when the game is playing.

We add triggers between the pipes, so when the bird passes throughthe pipes, the score will go up. this gameobject will be created in the parent pipe component as middle and will be a trigger i.e. (is trigger) box will be checked, and well add a cscript to this gameobject. We will use the onTriggerEnter2D function for the logic.
The logic cannot be directly added to the middle pipe script, we first create a tag for the logic script and then make a tag called "Logic", then in the middle pipe script add the following line that will look for the logic object with the abovemenetioned logic tag

GameObject.FindGameObjectWithTag("Logic").GetComponent<LogicScript>();

This operation adds the logic script to the middle pipe element during run time.

To manage a scene use UnityEngine.SceneManagament, we will use this for the onclick function of a button to restart the game.

