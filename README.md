# FlappyBirdClone

I am creating a clone of the game Flappy Bird as practice, using the Unity engine and C# scripts.

## Learning Journey

1. The assets were added to the scene. The sky and grass have been appropriately layered, the bird sprites have been separated into 3 spirtes. The bird sprite has been given a 2D polygon collider so it obeys the laws of physics. The ground has been given a 2D box collider so that the bird falls to the ground and not through the floor.

2. The first C# script has been written for the bird. I've added a private boolean isDead which, when set to true, will not allow the player to start flying again if they are dead. I have also created a private Rigidbody2D variable named rb2d which checks if it is attached to the bird when the game starts and stores the state inside the variable. 
In the void Update, if the player is not dead and clicks the mouse button, rb2d will add the force of the public float upForce which is set to 200f, allowing the bird to jump. I've used this to create a new Vector2 to pass to rb2d. The horizontal axis is set to 0 as the world moves horizontally rather than the player, but we call upForce on the X axis to allow the player to jump.