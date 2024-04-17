# Image Processing Subsystem

**Function:**

The goal of this subsystem is to receive and process the data from the camera sensor to determine the position and speed of the practice golf ball.  

**Constraints:**

| NO. | Constraint                                                          | Origin           |
|-----|---------------------------------------------------------------------|------------------|
| 1| Must be able to distinguish the golf ball from surroundings based on golf ball's color| System Requirment|
| 2| Must be able to extract the coordinates of the golf ball with an inch of accuracy| System Requirment|
| 3| Must be able to recieve the data and perform calculations in 500 ms| System Requirment|

1. In order for the system to properly detect the golf ball and extract the necessary information for aiming, the system needs to distinguish the golf ball
   from the rest of the image.
2. The program needs to use the coordinates from the camera to provide coordinates for aiming at the fishing line the golf ball is on which are about four
   inches apart at the start of the trajectory and know which variable height the ball is out which different by about seven inches. If the coordinates are
   off by an inch, the wire and height can be assumed to get the position of the golf ball.
3. The fastest speed of the golf ball is 1.95 seconds from empirical data from the customer. The ball needs to be detected in enough time for the team to
   aim the launcher and launch the projectile. This minimum allows time for the motors to make adjustments and fire after the information has been recieved
   and interpreted.

**Buildable Schematic**

The system is purely software. Any connections for the processor should be shown in that subsystems schematic.

A flow chart of the code is given below.

![Function](../Images/Image_Processing/Flow_Chart.PNG)

This shows the steps for each major calculation and what is necessary for each calculation. This process will be done twice to recieve two positions for the
speed calculation done by the processor.

**Analysis:**

*Detection*

The golf ball will be wrapped in foil and painted matte red. This will allow the object to be tracked using color. This can be done using a red, green, and
blue color detection. The boundaries for the color are determined and entered in as limits. For these purposes, red will have the highest boundaries while
green and blue will be much lower but still there to account for slight shading differences in the environment. These parameters and the image are then sent
to a function called inRange. This will apply a mask to the array of pixels repersenting the image with a maske to determine the objects with the color.
The results of such operations and algorithms can be seen below.

![Function](../Images/Image_Processing/Detecting_Red.png)

This can be adjusted to detect the ball at longer distances when the amount of pixels repersenting the object are smaller. The Big O analysis of this
function would be O(n) because it is an iterative function that will go through all of the pixels provided [1].


*Distance and Coordinates*

The distance of the object can be found using another iterative function for another linear algorithm. The camera returns an array with the depth of each 
pixel. This array is compared with the array holding the pixels that repersent the golf ball. The result is the depth of each pixel of the golf ball.

The object's coordinates can be determined through comparisons. Using edge of the field of view (FOV), the coordinates can be found. The pixels in between
the edge and the object can be counted. Using the width of each pixel, the total distance can be found. The pixel width can be found using the equations 

FOV width = 2 * tan(FOV/2) * distance and FOV height = 2 * tan(FOV/2) * distance

width per pixel = FOV width/horizontal resolution and height per pixel = FOV height/vertical resolution

For the distance of six feet the result will be

FOV width = 2 * tan(69/2) * 6 = 8.25 feet and FOV height = 2 * tan(42/2) * 6 = 4.61 feet

width per pixel = 8.25/1920 = 0.004296 feet/pixel * 12 = 0.05155 inches/pixel

height per pixel = 4.61/1080 * 12 = 0.004265 feet/pixel = 0.05118 inches/pixel

The amount of inches for the width and height of the pixels can be used to find out the x and y coordinates by multiplying the pixels by the numbers
provided. The accuracy of this method is high because it uses the size of the pixel based on the distance and should have enough pixels to find the
distance. This should allow about 0.1 inches of error for the coordinates. These calculations are basic arthemetic and should be O(1). Counting the pixels is another O(n) operation.

*Speed*

The camera that is being used is an 1920 by 1080 pixels. Benchmarks for the Jetson Nano Developer Kit show that for a 1920 by 1080 pixel image can process 
102 frames per second to find color and do several image alterations which is the same length as finding distance based on the Big O analysis. This means it
takes 9.8 ms to process the image information [2]. The camera takes in 30 frames per second so it takes 33.33 ms to get a new image. The USB cord connecting
the processor and camera processes data at 4.8 Gbs. Each pixel is 8 bits and has 3 colors so the total is 

8 * 3 * 1080 * 1920 = 0.4977 Gb. 

Taking the amount of data over the rate of transfer gives 

0.4977 Gb/4.8 Gbs = 103.68 ms. 

The arithmetic processes for determining speed and other calculations to send to the launcher are considered to have O(1). This means the most limiting time
factor is how long it takes to get two positions. 

33.33 ms + 103.68 ms + 9.8 ms + 33.33 ms + 103.68 ms + 9.8ms = 293.62 ms. 

This time period is well within the almost 1/4 time of the ball's travel given for the data to be collected and processed for the aiming and launching.

**Bill of Materials:**

This subsystem is implemented as part of the processor. No additional parts needed.

**References:**

[1] A. Rosebrock, “OpenCV and python color detection,” PyImageSearch, https://pyimagesearch.com/2014/08/04/opencv-python-color-detection/ 
(accessed Apr. 15, 2024). 

[2] F. Serzhenko, “✅ Jetson nano benchmarks for image processing,” fastcompression.com - GPU Image Processing Software,
https://www.fastcompression.com/blog/jetson-nano-benchmarks-image-processing.htm (accessed Apr. 15, 2024). 
