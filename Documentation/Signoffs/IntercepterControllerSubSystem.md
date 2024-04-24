# Interceptor Controller Subsystem

## **Function:**
![Elaboration Photo](../Images/Controllers/InterceptorController.png)

Figure 1: Interceptor Controller Subsystem

The goal of this subsystem is to take the analog outputs produced by the processor and the Arduino converts them the into digital outputs that can be used by the mechanical system to move the firing mechanism. The Arduino and Stepper Motor Driver will allow the specific motors the Mechanical Engineering team has picked to change speed, direction to one of the 30 set positions, and drop the ammunition when the firing sequence is activated .

## **Constraints:**

|No.|Constraint|Origin|
|--|------|-------|
|1|The Interceptor Controller shall move firing mechanism to 1 of 30 pre set locations |Conceptual Design|
|2|Must send back signal when aiming is finished to initiate firing sequence in processor| Conceptual Design |
|3|Shall receive 5V power supply from processor| Conceptual Design|
|4|Must change speed and direction of the motors in the Mechanical's section |Concepyual Design|



1.	Using the data sent by the processor it converts it to digital as coordinates that correspond to 1 of 30 set positions.
2.	After completing the movement to the desired position, a signal is sent back to the processor.
3.	Using the 5V pin from the processor to power the device.
4.  To be able to move to the correct coordinates the motors need to move in either direction along the x and y axis. This is also needed for testing the speed in which it must fire at and the speed it takes to move in to position.

## **Buildable Schematics:**

![Elaboration Photo](../Images/Controllers/Schematic3.png)

Figure 2: Buildable Schematic

## **Analysis:**
Arduino Analysis:

Due to the Arduinos variety of uses and applications it was the best choice to convert the analog data being provided from processor to digital logic that the mechanical system can understand. Shown in Figure 3 below we can see the JDIGITAL pins are the outputs of the Arduino but are the inputs for the mechanical system satisfying the first constraint. As for sending the signal back to the processer the analog side is used since that is the language the processer uses satisfying the third constraint. To ensure that the Arduino does not have any current going into the I/O pins a Stepper Motor is there to increase the current going into the motor to make it run as well as keep the current from going in reverse bias and frying the Arduino. Using these two devices speed, rotation, and direction can be changed. The speed is dictated my the power given to each motor *This measurement will be supplied by the ME team based on constraints and parameters of the competition*.

Stepper Motor Integration:

The Arduino UNO R3 seamlessly integrates with the TB6600 Stepper Motor Driver to control the interceptor's aiming mechanism [7]. Through GPIO communication, the Arduino UNO R3 commands the stepper motor driver to adjust the interceptor's position, aligning it with the golf ball's predicted path. Real-time trajectory data calculated by the Jetson Nano guides precise motor movements, ensuring accurate interception. The compatibility between theArduino UNO R3 and TB6600 Stepper Motor Driver facilitates seamless communication and system integration. The stepper motor will be put into a zero position. While it is in its zero position, the jetson nano can count how many steps the motor takes to determine the correct aiming position. This can apply for the X-Axis and Y-Axis of the system to be able to reset the interceptor back to the zero position after each time it aims and fires at the incoming golf ball [6].

![Elaboration Photo](../Images/Controllers/Arduino.png)

Figure 3[1]


## **Bill of Materials:**

|Device|Description|Used in which subsystem|Part Number| Manufacturer|Quantity|Price|Total|
|-------|---|---------|-------------|----|----|----|----|
| Arduino UNO R3 |converts analog data to digital inputs to move motors|Interceptor Controller Subsystem|A000066| Arduino|1|$27.60|$27.60|
|TB6600 Stepper Motor Driver|Regulates current and keeps from going reverse bias, and divides rotation into equal steps|Interceptor Controller Subsystem & Mechanical Subsystem|TB6600|DFRobot|3|$24.07|$72.21|
| | | | | | |Final Total|$99.81|

## **References:**
[1] Arduino, https://docs.arduino.cc/resources/pinouts/A000066-full-pinout.pdf (accessed Apr. 17, 2024). 

[2] Arduino, https://docs.arduino.cc/resources/schematics/A000066-schematics.pdf (accessed Apr. 17, 2024). 

[3] Arduino, https://docs.arduino.cc/resources/datasheets/A000066-datasheet.pdf (accessed Apr. 17, 2024). 

[4] Admin, Technology tutorials, https://toptechboy.com/arduino-tutorial-37-understanding-how-to-control-dc-motors-in-projects/ (accessed Apr. 17, 2024). 

[5] R. Sawkare, “Arduino Uno R3 with l293d motor driver,” Medium, https://vayuyaan.medium.com/arduino-uno-r3-with-l293d-motor-driver-550c4a65f612 (accessed Apr. 17, 2024). 

[6] “TB6600 Stepper Motor Driver,” Bulkman, https://bulkman3d.com/wp-content/uploads/2019/06/TB6600-Stepper-Motor-Driver-BM3D-v1.1.pdf (accessed Apr. 8, 2024).

[7] “TB6600 Stepper Motor Driver,” DFRobot, https://www.dfrobot.com/product-1547.html (accessed Apr. 8, 2024).

[8] S. Hall, Devcom. Devcom, 2024. S31 Paper Wad Interceptor Challenge 2024, Rulebook, (accessed Apr. 8, 2024).
