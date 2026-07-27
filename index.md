# Ball Tracking Robot
Replace this text with a brief description (2-3 sentences) of your project. This description should draw the reader in and make them interested in what you've built. You can include what the biggest challenges, takeaways, and triumphs from completing the project were. As you complete your portfolio, remember your audience is less familiar than you are with all that your project entails!
My project

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

<iframe width="560" height="315" src="https://www.youtube.com/embed/deRCS-uypKo?si=u50UgMhjb24PZ0-c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>n>
For my final milestone, I added code to make sure the detected object was also round, and code to search in the direction the ball last was when it moves out of frame. 
My biggest challenges were connecting my camera and getting my robot to recognize the ball. For my camera, I had to switch to a different port on my raspberry pi to connect it with, and for the recognition I had to experiment with different bounds for the red color in the code to account for the lights reflecting off of it.
I learned a lot about how OpenCV works, such as about the bounds defining a color, and color masking. I also learned how ultrasonic sensors work, and how to convert that value into centimeters to make it easier to work with. Overall, throughout the project I learned a lot about debugging, especially with wiring, such as the multimeter to check where power may or may not be going through. 
I'd hope to learn more about other sensors, such as a gyro sensor for more accurate navigation and turning. 

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



# Second Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/dqM9WtTb2UU?si=RHYvApd_0N4gP6nQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

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
Ultrasonic Sensor Testing Code:
```c++
import RPi.GPIO as GPIO
import time
GPIO.setmode(GPIO.BCM)

TRIG_PIN = 26
ECHO_PIN = 16

GPIO.setup(TRIG_PIN, GPIO.OUT)
GPIO.setup(ECHO_PIN, GPIO.IN)
GPIO.output(TRIG_PIN, GPIO.LOW)

time.sleep(2)

GPIO.output(TRIG_PIN, GPIO.HIGH)

time.sleep(0.00001)

GPIO.output(TRIG_PIN, GPIO.LOW)

while GPIO.input(ECHO_PIN) ==0:
    pulse_send=time.time()
while GPIO.input(ECHO_PIN) ==1:
    pulse_received=time.time()
   
pulse_duration=pulse_received - pulse_send
pulse_duration=pulse_duration/2

distance = 34300 * pulse_duration #speed of sound (cm/s) = 34300
distance = round(distance,2)

print ("object is at", distance, "cm from the ultrasonic sensor")

GPIO.cleanup()
```

Motor Testing Code:
```c++
import RPi.GPIO as GPIO
import cv2
import numpy as np

GPIO.setmode(GPIO.BCM)

MOTOR1B=24 # LEFT motor
MOTOR1E=23

MOTOR2B=22 # RIGHT motor
MOTOR2E=17

GPIO.setup(MOTOR1B, GPIO.OUT)
GPIO.setup(MOTOR1E, GPIO.OUT)

GPIO.setup(MOTOR2B, GPIO.OUT)
GPIO.setup(MOTOR2E, GPIO.OUT)

while(True):
    userInput = input()
   
    if(userInput == 'w'):
        GPIO.output(MOTOR1B,GPIO.HIGH)
        GPIO.output(MOTOR1E,GPIO.LOW)
        GPIO.output(MOTOR2B,GPIO.HIGH)
        GPIO.output(MOTOR2E,GPIO.LOW)
   
    if(userInput == 'a'):
        GPIO.output(MOTOR1B,GPIO.LOW)
        GPIO.output(MOTOR1E,GPIO.LOW)
        GPIO.output(MOTOR2B,GPIO.HIGH)
        GPIO.output(MOTOR2E,GPIO.LOW)
       
    if(userInput == 's'):
        GPIO.output(MOTOR1B,GPIO.LOW)
        GPIO.output(MOTOR1E,GPIO.HIGH)
        GPIO.output(MOTOR2B,GPIO.LOW)
        GPIO.output(MOTOR2E,GPIO.HIGH)
   
    if(userInput == 'd'):
        GPIO.output(MOTOR1B,GPIO.HIGH)
        GPIO.output(MOTOR1E,GPIO.LOW)
        GPIO.output(MOTOR2B,GPIO.LOW)
        GPIO.output(MOTOR2E,GPIO.LOW)

    if(userInput == 'x'):
         GPIO.output(MOTOR1B,GPIO.LOW)
         GPIO.output(MOTOR1E,GPIO.LOW)
         GPIO.output(MOTOR2B,GPIO.LOW)
         GPIO.output(MOTOR2E,GPIO.LOW)
```

The finished program:
```c++
import cv2
from picamera2 import Picamera2
import time
import numpy as np
import RPi.GPIO as GPIO
import cv2
import numpy as np
from gpiozero import PWMOutputDevice

GPIO.setmode(GPIO.BCM)
SPEED = 0.4

GPIO_TRIGGER2 = 9     #FRONT ultrasonic sensor
GPIO_ECHO2 = 1
#

motor1B = PWMOutputDevice(24, frequency=100) # LEFT Forward
motor1E = PWMOutputDevice(23, frequency=100) # LEFT Backward

motor2B = PWMOutputDevice(22, frequency=100) # RIGHT Forward
motor2E = PWMOutputDevice(17, frequency=100)

GPIO.setup(GPIO_TRIGGER2,GPIO.OUT)  # Trigger 2
GPIO.setup(GPIO_ECHO2,GPIO.IN)  # Echo 2
GPIO.output(GPIO_TRIGGER2, False)

def sonar(GPIO_TRIGGER,GPIO_ECHO):
    start=0                    
    stop=0
    GPIO.setup(GPIO_TRIGGER,GPIO.OUT)  # Trigger
    GPIO.setup(GPIO_ECHO,GPIO.IN)      # Echo
     
    GPIO.output(GPIO_TRIGGER, False)   # Set trigger to False (Low)
     
    time.sleep(0.01)                   # Allow module to settle

    #while distance > 5, Send 10us pulse to trigger
    GPIO.output(GPIO_TRIGGER, True)
    time.sleep(0.00001)
    GPIO.output(GPIO_TRIGGER, False)
    begin = time.time()
    while GPIO.input(GPIO_ECHO)==0 and time.time()<begin+0.05:
        start = time.time()
     
    while GPIO.input(GPIO_ECHO)==1 and time.time()<begin+0.1:
        stop = time.time()
     
    elapsed = stop-start # Calculate pulse length
   
    distance = elapsed * 34300 # Distance pulse traveled in that time is time multiplied by the speed of sound (cm/s)
     
   
    distance = distance / 2 # That was the distance there and back, so take half of the value

   
    return distance # Reset GPIO settings, return distance (in cm) appropriate to be used for robot movement

def stop():
#     GPIO.output([MOTOR1B, MOTOR1E, MOTOR2B, MOTOR2E], GPIO.LOW)
    motor1B.value = 0
    motor1E.value = 0
    motor2B.value = 0
    motor2E.value = 0


def left():
    # Left motor backward/stop, Right motor forward
    motor1B.value = 0
    motor1E.value = SPEED
    motor2B.value = SPEED
    motor2E.value = 0

def right():
    # Left motor forward, Right motor backward/stop
    motor1B.value = SPEED
    motor1E.value = 0
    motor2B.value = 0
    motor2E.value = SPEED

def forward():
    motor1B.value = SPEED
    motor1E.value = 0
    motor2B.value = SPEED
    motor2E.value = 0
   

# Camera setup
picam2 = Picamera2()

# Set dimensions for the preview
picam2_config = picam2.create_preview_configuration(
    main={"format": 'XRGB8888', "size": (320, 240)},
    raw={"size": (320, 240)}
   
)

picam2.configure(picam2_config)
# picam2.video_configuration.controls.FrameRate = 25.0
flag = 0 #SEARCHING: 0: left turn for last location of ball, 1: right turn for last location of ball
flag_reroute = -1 #REROUTE SEARCHING  -1: No reroute, 0:reroute left , 1: reroute right

picam2.start()
time.sleep(2)
 

# Define Red Color Range in HSV (moved outside loop for performance)
lower_red1 = np.array([0, 100, 35])
upper_red1 = np.array([10, 255, 255])
lower_red2 = np.array([170, 100, 35])
upper_red2 = np.array([180, 255, 255])

# Structural element for morphology
kernel = np.ones((5, 5), np.uint8)

# Tracking Parameters
FRAME_CENTER_X = 320   # 640 horizontal pixels / 2
DEADZONE = 200          # Left/Right deviation allowed before steering (in pixels)
MIN_AREA = 800         # Min object pixel size to prevent chasing random noise

CIRCULARITY_THRESH = 0.35   # 1.0 = perfect circle
FILL_RATIO_THRESH = 0.35
def roundness_scores(contour):
    """Return (circularity, fill_ratio) for a contour.
    circularity: 4*pi*Area / Perimeter^2  -> 1.0 for a perfect circle
    fill_ratio: Area / area_of_min_enclosing_circle -> 1.0 if blob fills that circle
    """
    area = cv2.contourArea(contour)
    perimeter = cv2.arcLength(contour, True)
 
    if perimeter == 0:
        return 0.0, 0.0
 
    circularity = 4 * np.pi * area / (perimeter ** 2)
 
    (x, y), radius = cv2.minEnclosingCircle(contour)
    circle_area = np.pi * (radius ** 2)
    fill_ratio = area / circle_area if circle_area > 0 else 0.0
 
    return circularity, fill_ratio
 
 
def is_round(contour, circularity_thresh=CIRCULARITY_THRESH, fill_ratio_thresh=FILL_RATIO_THRESH):
    circularity, fill_ratio = roundness_scores(contour)
    return circularity > circularity_thresh and fill_ratio > fill_ratio_thresh

try:
    while True:
        img = picam2.capture_array()
       
        # Convert
        img_rgb = cv2.cvtColor(img, cv2.COLOR_BGRA2RGB)
       
        # Convert from BGR to HSV
        hsv_frame = cv2.cvtColor(img_rgb, cv2.COLOR_BGR2HSV)

        # Create binary masks
        mask1 = cv2.inRange(hsv_frame, lower_red1, upper_red1)
        mask2 = cv2.inRange(hsv_frame, lower_red2, upper_red2)
        full_red_mask = cv2.bitwise_or(mask1, mask2)

        # Smooth out background specks and fill holes
        full_red_mask = cv2.erode(full_red_mask, kernel, iterations=1)
        full_red_mask = cv2.dilate(full_red_mask, kernel, iterations=1)
       
        contours, _ = cv2.findContours(full_red_mask, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)

        target_found = False

        # Filter the original output
        red_filtered_output = cv2.bitwise_and(img_rgb, img_rgb, mask=full_red_mask)
       
        if contours:
            # Locate the largest red object in frame
            sorted_contours = sorted(contours, key=cv2.contourArea, reverse=True)
 
            largest_contour = None
            for c in sorted_contours:
                if cv2.contourArea(c) > MIN_AREA and is_round(c):
                    largest_contour = c
                    break
 
            if largest_contour is not None:
                target_found = True
                M = cv2.moments(largest_contour)
               
                if M["m00"] != 0:
                    # Calculate centroid by dividing spatial sum over total area
                    cX = int(M["m10"] / M["m00"])
                    cY = int(M["m01"] / M["m00"])
                   
                    # Visual feedback indicators on our screen
                    cv2.circle(img_rgb, (cX, cY), 7, (0, 255, 0), -1)
#                     cv2.putText(img_rgb, "Red Target", (cX - 25, cY - 25), cv2.FONT_HERSHEY_SIMPLEX, 0.5, (0, 255, 0), 2)

                    # Debug: show roundness scores next to the target
                    circ, fill = roundness_scores(largest_contour)
                    cv2.putText(img_rgb, f"circ:{circ:.2f} fill:{fill:.2f}",
                                (cX - 40, cY - 25), cv2.FONT_HERSHEY_SIMPLEX,
                                0.4, (0, 255, 0), 1)
                   
                    # --- Target Tracking Decision Tree ---
                    error_x = cX - FRAME_CENTER_X
                   
                    if error_x > DEADZONE:
                        flag = 1 # Last seen on the right (if robot loses ball)
                        print(f"Target right ({error_x}px). Turning Right.")
                        right()
                    elif error_x < -DEADZONE:
                        flag = 0 # Last seen on the left (if robot loses ball)
                        print(f"Target left ({error_x}px). Turning Left.")
                        left()
#                     else:
#                         print("Target centered! Stopping.")
#                         stop()
                    else:
                        # Ball is centered horizontally - check front ultrasonic
                        # sensor before driving forward toward it.
                        distance = sonar(GPIO_TRIGGER2, GPIO_ECHO2)
                       
                        if(error_x < 0):
                            print("setting flag left")
#                             print(error_x, FRAME_CENTER_X)
                            flag = 0 #If ball is lost while to the left of the center, assign flag = 0
                        elif(error_x >= 0):
                            flag = 1 #If ball is lost while to the right of the center, assign flag = 1
                            print("setting flag right")
                        if distance > 7:
                            print(f"Distance {distance:.1f}cm. Moving forward.")
                            forward()
                        else:
                            print(f"Distance {distance:.1f}cm. Stopping.")
                            stop()
#                         forward()

        if not target_found:
            stop()
#             print("No red target detected")
            print("Finding ball, turning")
            if flag == 0: # If last seen location was on the left, search by turning left
                print("Searching left")
                left()
#                 time.sleep(0.04)
#                 stop()
            elif flag == 1: # If last seen location was on the right, search by turning right
                right()
                print("Searching right")
#                 time.sleep(0.04)
#                 stop()
#                    
        # Display windows
        cv2.imshow("Original Output", img_rgb)
#         cv2.imshow("Red Masked Output", red_filtered_output)
#         cv2.imshow("Red Mask", full_red_mask)

        if cv2.waitKey(1) & 0xFF == ord('q'):
            break

except Exception as e:
    print(f"An error occurred: {e}")

finally:
    stop()
    GPIO.cleanup()
    picam2.stop()
    picam2.close()
    cv2.destroyAllWindows()
    print("Application closed.")
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
