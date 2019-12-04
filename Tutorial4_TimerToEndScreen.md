# Timer to Endscreen Tutorial

In this tutorial we will create a timer that changes scene when it has elapsed. This tutorial follows the previous [tutorial](https://github.com/ie2990/IsabelElia_CW1/blob/master/Tutorial3_HoldObject.md), please complete it first before continuing with this one.

## Setup

We will start setting up this tutorial by creating a new scene called `GameOver`. If you wish, you can edit this scene using a `Panel` as demonstrated in [the first tutorial](https://github.com/ie2990/IsabelElia_CW1/blob/master/Tutorial1_StartMenu.md) and add text saying "Game Over" instead of the `Play` button. Or you could just leave it blank for the purposes of the tutorial.

In the `FpsController` scene, we are going to create a text object that will display the timer. To do this, simply create a canvas by right clicking on the Hierachy, selecting UI>Text. Rename the Text Object to `CountdownTxt`, and in the inspector, change the `Text` to say "00" for now.

You can now edit the placement and style of the text if you choose to do so. I suggest something bold and easy to see in a contrasting font colour than the scene. I went for font size 80 and the vertex colour to be black. I also decided to move it to the upper centre portion of the screen.

## Creating a Timer

Create a new script called `Timer` and open it.

Firstly, we need to ensure that the script is using the `SceneManagement` and `UI` inputs.

Next we will need to create some variables. The variables we will want to be monitering and changing are the time we begin the countdown timer on and the time that currently needs to be displayed to the player.

```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;
using UnityEngine.UI;


public class Timer : MonoBehaviour
{

    public float startingTime = 10f;
    public float currentTime = 0f;


}
```

Now that we've created these variables, let's utilise them. At the start of the scene, we want the time to display the starting time. To ensure this we make the `currentTime` the `startingTime`.

```
    private void Start()
    {
        currentTime = startingTime;
    }
```

Moving into the `Update()` method, as the game progresses, we want the time to display the `currentTime` and decrease the value of that by 1 each second. To do this we must employ `Time.deltaTime` to ensure the value is reduced each second rather than each frame.

```
    private void Update()
    {
        currentTime -= 1 * Time.deltaTime;
        
```

## Timer text

Now that we've set up the timer, let's display this using the `CountdownTxt` we created.

To do this we need to add in a new variable under the `startingTime` and `currentTime` ones we previously made.

```
 [SerializeField] Text timerText;
```

Then in the update, we want to add in:

```
timerText.text = currentType.ToString();
```


## Changing scenes

When the timer reaches 0, we want to display the `GameOver` scene. To do this we simply need to create an `if` variable that changes scene once the `currentTime` reaches 0.


