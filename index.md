# Ball Tracking Robot
Replace this text with a brief description (2-3 sentences) of your project. This description should draw the reader in and make them interested in what you've built. You can include what the biggest challenges, takeaways, and triumphs from completing the project were. As you complete your portfolio, remember your audience is less familiar than you are with all that your project entails!

You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:
```HTML 
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->
```

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Michelia P | Saint Francis High School | Mechanical Engineering | Incoming Junior

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://youtu.be/deRCS-uypKo?si=ozgSyJpgUowOZ7sO" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
For my final milestone, I added code to make sure the detected object was also round, and code to search in the direction the ball last was when it moves out of frame. 
My biggest challenges were ..............
I learned a lot about how OpenCV works, such as about the bounds defining a color, and color masking. I also learned how ultrasonic sensors work, and how to convert that value into centimeters to make it easier to work with. Overall, throughout the project I learned a lot about debugging, especially with wiring, such as the multimeter to check where power may or may not be going through. 
I'd hope to learn more about other sensors........

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



# Second Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://youtu.be/dqM9WtTb2UU?si=JHxGaZzCtH7Smqpm" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For my second milestone, I added a camera and two more ultrasonic sensors to my robot. I used OpenCV to recognize the red coloring of the ball, then set some parameters for the tracking of the ball, such as a "deadzone" which is a section in the middle that the ball should stay in, and a minimum area of the ball to prevent the robot from tracking some other random red thing. Then, I used the ultrasonic sensor to get the distance between the ball and the robot, and to have the robot move till its around or closer than 7 cm to the ball.

I was surprised to learn that with color spaces, HSV(Hue Saturation Value) is better for tracking colored objects than RGB(Red Green Blue). The reason for this is that HSV takes the lighting more into account, since the color is measured seperate from the lighting. 

I faced difficulty with getting the camera to connect to the pi. At first, I tried to connect a camera port, but the Raspberry Pi wouldn't recognize any camera connected to it. Eventually, I tested this with another camera and was able to conclude that the camera port itself was faulty. In this process, I also found out that I was using an old OS which I had thought could've been causing the issue with the camera. It's now updated for to the Trixie OS. Tuning the color bounds for red also took some experimenting.
Before my final milestone, I'd like to add code for the robot to search for the ball if it goes out of frame via flags.

# First Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/s6c-uwc9rKY?si=y6-t750BN_sJyhXn" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

```HTML 
<!---For your first milestone, describe what your project is and how you plan to build it. You can include:
- An explanation about the different components of your project and how they will all integrate together
- Technical progress you've made so far
- Challenges you're facing and solving in your future milestones
- What your plan is to complete your project-->
```

My Project is the Ball Tracking Robot. I plan to put together a Chassis, an ultrasonic sensor, a camera, and a Raspberry Pi to create a robot that uses color to recognize a red ball and navigate towards it. It'll use the camera and the OpenCV library to detect the ball, and the ultrasonic sensor to get the distance from the ball. 

So far, I've finished building my chassis, and wiring the motors and the ultrasonic sensor. The motors are currently controlled via WASD keys on my computer, and I've also created a simple program to test the Ultrasonic sensor by printing the distance between the sensor and the object closest to it. 

I had some difficulty with my motor driver where the motors wouldn't move despite the power going through the right places(as confirmed by a multimeter), but fixed this by siwtching to a different one. The problem turned out to be that the original motor driver needed 5 volts, when the Raspberry Pi only supplied 3.3. Right now, I'm running into issues with the camera. When I connected it to my computer to check, it wouldn't show up there either, so it's safe to assume that it was an issue with the camera itself. 

My next steps will be to get and attach a new camera, and then use OpenCV to code it to recognize red.

# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  Serial.println("Hello World!");
}

void loop() {
  // put your main code here, to run repeatedly:

}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
