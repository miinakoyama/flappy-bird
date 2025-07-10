# Flappy Bird

This is a simple Flappy Bird game created with Unity.

## How to Play

The goal of the game is to navigate the bird through a series of pipes without hitting them.

*   **Jump:** Press the spacebar to make the bird flap its wings and gain height.
*   **Scoring:** You get a point for each pipe you successfully pass through.
*   **Game Over:** The game ends if the bird hits a pipe or the ground.

## Scripts

### BirdScript.cs

This script controls the behavior of the bird.

*   **`flapStrength`:** A public float that determines the upward force applied to the bird when it flaps.
*   **`Start()`:**  This method is called when the script instance is being loaded. It finds the `LogicScript` in the scene and assigns it to the `logic` variable.
*   **`Update()`:** This method is called once per frame. It checks for a spacebar press and, if the bird is alive, applies an upward velocity to the `Rigidbody2D` component.
*   **`OnCollisionEnter2D(Collision2D collision)`:** This method is called when the bird collides with another object. It triggers the `gameOver` function in the `LogicScript` and sets the `birdIsAlive` flag to false.

### LogicScript.cs

This script manages the game's logic, such as scoring and game over.

*   **`playerScore`:** An integer that keeps track of the player's score.
*   **`scoreText`:** A `Text` component to display the score.
*   **`gameOverScreen`:** A `GameObject` that is activated when the game is over.
*   **`addScore(int scoreToAdd)`:** A public method to increase the player's score.
*   **`restartGame()`:** A public method to reload the current scene, effectively restarting the game.
*   **`gameOver()`:** A public method that activates the game over screen.

### PipeMoveScript.cs

This script controls the movement of the pipes.

*   **`moveSpeed`:** A public float that determines the speed at which the pipes move to the left.
*   **`deadZone`:** A public float that defines the x-position at which the pipe is considered "off-screen" and should be destroyed.
*   **`Update()`:** This method is called once per frame. It moves the pipe to the left and checks if it has gone off-screen.

### PipeSpawner.cs

This script is responsible for spawning new pipes.

*   **`pipe`:** A reference to the pipe prefab to be spawned.
*   **`spawnRate`:** A float that determines the time interval between pipe spawns.
*   **`timer`:** A private float to keep track of the time since the last spawn.
*   **`hightOffset`:** A public float that controls the vertical range in which the pipes can spawn.
*   **`Start()`:** This method is called when the script instance is being loaded. It calls the `spawnPipe()` method to create the first pipe.
*   **`Update()`:** This method is called once per frame. It increments the timer and, when it reaches the `spawnRate`, calls `spawnPipe()` and resets the timer.
*   **`spawnPipe()`:** This method instantiates a new pipe at a random height within the defined range.

## Future Improvements

*   Add a scoring system that increases with difficulty.
*   Implement different types of obstacles.
*   Add sound effects and music.
*   Create a main menu screen.
