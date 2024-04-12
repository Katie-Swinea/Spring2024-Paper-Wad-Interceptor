# **Function:**

The Jetson Nano plays a pivotal role in this project as the central processing unit responsible for receiving, analyzing, and interpreting data from the image-detecting system to calculate and aim the interceptor. Its primary function revolves around processing data related to a golf ball's trajectory in real time. The Jetson Nano serves as the brain of the system, consolidating data from the local camera that passes the data to the jetson.

Moreover, the Jetson Nano is instrumental in controlling the firing mechanism of the golf ball interceptor. Through the data it calculates and processes, it determines the optimal timing for activating the interceptor, ensuring precise targeting of the golf ball, particularly within the designated "kill zone."

The Jetson Nano will also contain a pause switch, this pause switch is to stop the mechanism from firing anymore projectiles. It will be a physical switch that will interact with the Jetson Nano directly and alter scripts inside the Jetson to stop functionality.

![System](../Images/MainProcessor/JetsonNanoGPIODiagram.png)

Figure 1: Jetson Nano Wiring Schematic

![System](../Images/MainProcessor/Switch_Buildable_2.png)
Figure 2: Pause switch integration

## **Constraints:**

| NO. |	Constraint | Origin |
|-----|------------|--------|
| 1	| Time Constraints - Real-time data processing for trajectory prediction | System Constraint |
| 2	| Processing Speed - Optimization for efficient calculations | System Constraint |
| 3	| Signal Interpretation Challenges - Ensuring accurate data interpretation | Programming Constraint |
| 4	| Resource Utilization - Preventing overload of system resources | System Constraint |



## **Fulfilling Constraints:**

**Time Constraints:** Real-time processing of sensor data and trajectory calculations impose time constraints on the Jetson Nano. Since it has to be able to detect and calculate the proper position of the ball. Its 1.43GHz quad-core ARM Cortex-A57 the processor needs to be able to receive, process, calculate the interceptor’s path, and aim the interceptor before the golf ball gets too far down the string [3]. The programs and data transmission needs to be optimized for an accurate and efficient system to be able to run fast enough. Delays in data acquisition, processing, or interceptor firing may affect the interception accuracy dramatically. [2]

**Processing Speed:** Complex calculations and simultaneous tasks may strain the processing capabilities of the Jetson Nano, potentially leading to performance bottlenecks. Optimizing algorithms and utilizing hardware and multi-core techniques can help minimize processing speed limitations.

**Signal Interpretation Challenges:** Variability in wireless signal strength, interference, and environmental factors may pose challenges in accurately interpreting sensor data. The Jetson Nano needs to be able to filter all signals, determine accurate data that it receives and predict the golf balls trajectory will require enormous testing and a versatile system. An accurate signal-processing algorithm and error-handling backup codes are going to be essential for creating reliable data for the system.

**Resource Utilization:** With 4GB of LPDDR4 RAM, the Jetson Nano offers ample memory for concurrent tasks. However, efficient resource management is imperative to prevent resource overload. Optimization strategies focus on minimizing memory usage and CPU load, preserving system responsiveness.



## **Execution Using Jetson Nano:**

Python remains the primary programming language for interfacing with the Jetson Nano due to its versatility and extensive libraries. Additionally, C++ may be employed for computationally intensive tasks, leveraging the Jetson Nano's GPU for accelerated computations. [5]

**Hardware Configuration:** The Jetson Nano interfaces with the other hardware components with the GPIO pins. GPIO pins such as GPIO05, GPIO06, GPIO13, GPIO12, and GPIO18 facilitate flexible input/output operations, accommodating sensor connections and interceptor control. While using GPIO02 and GPIO03 for the SCL and SDA data.

**Programs and Tasks:** Custom Python scripts orchestrate various system tasks, including signal processing, trajectory calculations, and interceptor control. Multithreading may be applied to enable concurrent execution of tasks, maximizing system efficiency.

**Data Processing and Calculations:** Upon receiving the image detection data, the Jetson Nano executes trajectory calculations to determine the golf ball's velocity, height, distance, and direction. Mathematical algorithms will be used to accurately determine the data.

The height calculations will need the height of the camera, the image height of the bounding box in pixels, and the distance from the camera to the object. The physical height of the two possible positions [1].
~~~math
Object Height = ( Physical Height * Image Height )/( Distance * Sensor Height )
~~~

The Speed calcuations will be taking the distance or position of the object over time [1]. The frames of the objects lcoation can calculate the speed using the following equation.
~~~math
Speed = Change in Distance / Change in Time
~~~

The distance calcuation will need to take the time interval between frames the object has traveled using the following equation to properly find the distance from the interceptor [1].
~~~math
Distance = Speed * Time interval
~~~



**Signal Interpretation:** The Jetson Nano will need signal processing techniques to interpret wireless sensor data accurately. Noise filtering and error correction mechanisms enhance signal clarity, enabling precise trajectory prediction.

**Control of Golf Ball Interceptor Shooter:** Based on the calculated trajectory data, the Jetson Nano will control the timing and activation of the golf ball interceptor shooting mechanism. It needs to have the interceptor to be properly aligned towards the golf ball's predicted path, and fire at the appropriate time to hit the ball mid-air. This could use preset fire positions to optimize the interception process.




## **Board Component Integration:**

**Pause Switch Analysis**

The pause switch component has many different switches that can be chosen. Switches range between single pole, single throw, and upwards. The switch that needs to be implemented for the pause switch should be a single pole double-throw switch that has a two on functions and an off function. This will ensure that with one connection the processor will be receiving 5V, which will count as a binary one, and when the switch is off the processor will be connected to ground which will be interpreted as a binary zero. The switch that was chosen for this task is the NTE Electronics, 54-571-2 [8]. This switch is rated for 20A and 12VDC which will be more than enough for this simple task. The other main portion of the pause switch is the implementation in the code of the processor. Because a processor has not been chosen now it is not possible to say exactly how this will be implemented, but pseudocode can be written to make the coding process easier. To be clear when the pause switch is on 5V or equivalent will be allowed to pass and when it is off the circuit will not be connected. This input will be interpreted as a variable and when the circuit is on the processor will be allowed to collect the data from the sensors. When the switch is off the processor will be in the pause state where it can not do anything but wait for the switch to be turned on.

**Stepper Motor Integration**

The Jetson Nano seamlessly integrates with the TB6600 Stepper Motor Driver to control the interceptor's aiming mechanism [7]. Through GPIO communication, the Jetson Nano commands the stepper motor driver to adjust the interceptor's position, aligning it with the golf ball's predicted path.

Real-time trajectory data calculated by the Jetson Nano guides precise motor movements, ensuring accurate interception. The compatibility between the Jetson Nano and TB6600 Stepper Motor Driver facilitates seamless communication and system integration.

The stepper motor will be put into a zero position. While it is in its zero position, the jetson nano can count how many steps the motor takes to determine the correct aiming position. This can apply for the X-Axis and Y-Axis of the system to be able to reset the interceptor back to the zero position after each time it aims and fires at the incoming golf ball [6].


## **Cost Analysis:**
|Name|	Count|	Price |	Total |
|---|---|---|---|
|Jetson Nano 945-13450-0000-000|	1|	$209.00|	$209.00|
|TB6600 Stepper Motor Driver|	3	|$20.00	|$60.00|
| | | | 			~$270.00|

The Jetson Nano offers an affordable yet powerful solution for system control, priced at $209.00 [4]. Coupled with the TB6600 Stepper Motor Driver which cost $20.00 each [6], the total cost amounts to ~$270.00, ensuring cost-effectiveness without compromising performance for doing image processing calculations.



## **References:**

[1] N. shukla, “A review on image based target distance & height ...,” Research Publish, https://www.researchpublish.com/upload/book/A Review on Image Based Target Distance-1172.pdf (accessed Apr. 11, 2024). 

[2] “NVIDIA® Jetson Nano 4GB development kit,” OKdo, https://www.okdo.com/us/p/nvidia-jetson-nano-4gb-development-kit/ (accessed Apr. 11, 2024).

[3] “Jetson nano developer kit by Nvidia: 945-13450-0000-000,” Arrow.com, https://www.arrow.com/en/products/945-13450-0000-000/nvidia (accessed Apr. 11, 2024).

[4] Walmart, https://www.walmart.com/ip/NVIDIA-Jetson-Nano-Developer-Kit/480691437?wmlspartner=wlpa&selectedSellerId=11832&adid=22222222227480691437_11832_146045225401_18612869729&wl0=&wl1=g&wl2=c&wl3=628562918858&wl4=aud-2225087348107%3Apla-1838654855916&wl5=1025954&wl6=&wl7=&wl8=&wl9=pla&wl10=117079748&wl11=online&wl12=480691437_11832&veh=sem&gad_source=1&gclid=Cj0KCQjwlN6wBhCcARIsAKZvD5jwTYJgdMQqUTOA0_bi87XId5dExtSr0RrJbe0Hu2oBk9rWw8MvXPMaAoahEALw_wcB (accessed Apr. 11, 2024).

[5] Dr. M. Nazeer, M. Qayyum, and A. Ahad, “Real time object detection and recognition in machine learning using Jetson Nano,” SSRN, https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4286087 (accessed Apr. 11, 2024). 

[6] “TB6600 Stepper Motor Driver,” Bulkman, https://bulkman3d.com/wp-content/uploads/2019/06/TB6600-Stepper-Motor-Driver-BM3D-v1.1.pdf (accessed Apr. 8, 2024).

[7] “TB6600 Stepper Motor Driver,” DFRobot, https://www.dfrobot.com/product-1547.html (accessed Apr. 8, 2024).

[8] “Toggle switches,” NTE Electronics, https://www.nteinc.com/switches/pdf/toggle-std.pdf (accessed Apr. 6, 2024).
