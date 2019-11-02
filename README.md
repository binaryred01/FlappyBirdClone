# FlappyBirdClone

I am creating a clone of the game Flappy Bird as practice, using the Unity engine and C# scripts.

## Learning Journey

1. The assets were added to the scene. The sky and grass have been appropriately layered, the bird sprites have been separated into 3 spirtes. The bird sprite has been given a 2D polygon collider so it obeys the laws of physics. The ground has been given a 2D box collider so that the bird falls to the ground and not through the floor.

2. The first C# script has been written for the bird. I've added a `private boolean isDead` which, when set to `true`, will not allow the player to start flying again if they are dead. I have also created a `private Rigidbody2D` variable named `rb2d` which checks if it is attached to the bird when the game starts and stores the state inside the variable. 
In void `Update`, if the player is not dead and clicks the mouse button, `rb2d` will add the force of the `public float upForce` which is set to `200f`, allowing the bird to jump. I've used this to create a new `Vector2` to pass to `rb2d`. The horizontal axis is set to `0` as the world moves horizontally rather than the player, but we call `upForce` on the X axis to allow the player to jump.

3. I have added animations to the bird. This was done by using the animation window in Unity to create three animations; `Idle`, `Flap`, `Dead`. I've assigned each sprite to each animation. Next I used the animator tab to create new trigger parameters; again `Idle`, `Flap` and `Dead`. These are then linked together with transitions. `Idle` will transition to `Dead` with no exit time because I want the bird animation to loop while in `Idle`. Next I created a transition from `Idle` to `Flap` and a transition back from `Flap` to `Idle` with an exit time so that the bird doesn't keep flapping.
**Note that the record button must be selected in Unity while creating all these actions or they will not work.**
Next, I modified the Bird script so that these animations all play together when the game is run. To do this, I added a `private Animator` variable called `anim`. In `Start`, I store a reference to it using `GetComponent` allowing me to send commands to the animator component using the `anim` variable. Now when I add force in Update, the animation will play by calling `SetTrigger("Flap")` on `anim`. To transition to the dead state, I do the same within `OnCollisionEnter2D` but set the trigger to the string `"Dead"`.

4. Added Score and Game Over UI to the scene. This is done by creating a new text object in the scene (called ScoreText) which in turn creates a canvas that is a parent of the text. I deleted the events system that also gets created as I will not be interacting with the UI. In the inspector I've set the font to the imported font, changed the text size and allowed horizontal and vertical overflow so that the text goes outside the text box. Also added a shadow component to the text so it's visible on all backgrounds. Changed text colour to white. Picked centre and middle alignment for the box. Set bottom-centre anchor preset and adjusted position for Y axis. I duplicated this for the GameOverText and PlayAgainText and adjusted settings accordingly. The PlayAgainText is a child of the GameOverText. Finally, I've disabled the GameOverText so it doesn't appear when you start the game.

5. 




