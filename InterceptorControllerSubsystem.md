# Interceptor Controller Subsystem

## **Function:**
![Elaboration Photo](../Images/Controllers/InterceptorController.png)
Figure 1: Interceptor Controller Subsystem

The goal of this subsystem is to take the outputs from the processer and convert them into inputs that can be used for the mechanical system. 

## **Constraints:**

|No.|Constraint|Origin|
|--|------|-------|
|1|The Interceptor Controller shall move firing mechanism to 1 of 30 locations |Conceptual Design|
|2|Must send back signal when aiming is finished to initiate firing | Conceptual Design |
|3|Must turn initiate firing| Conceptual Design
|4|Must be powered with a 6 to 20V voltage source | Device Constraint|
|5|Maximum current per I/O pin is 20mA| Device Constraint|
|6|Maximum current per +3.3V pin is 50mA| Device Constraint|
|7|Maximum voltage to L293D motor control chip 36V| Device Constraint|




1.	Using the data sent by the processor it converts it digital as coordinates that correspond to 1 of 30 set positions.
2.	After completing the movement to the desired position, a signal is sent back to the processor.
3.	After sending a signal from the Interceptor Controller another signal is sent back from the processor to initiate the firing of the projectile.
4.	To ensure that the device is powered safely a 6 to 20V power supply is needed but, has a barrel plug connector that works with a standard 9V battery.
5.	Per the data sheet the I/O pins are only regulated for 20mA.
6.	Per the data sheet the +3.3V pins are only regulated for 50mA.
7.	Per the data sheet a max of 36V can be applied.


## **Buildable Schematics:**

![Elaboration Photo](../Images/Controllers/Schematic2.png)
Figure 2: Buildable Schematic [5]

## **Analysis:**
Arduino Analysis:
Due to the Arduinos variety of uses and applications it was the best choice to convert the analog data being provided from processor to digital logic that the mechanical system can understand. Shown in Figure 3 below we can see the JDIGITAL pins are the outputs of the Arduino but are the inputs for the mechanical system satisfying the first constraint. As for sending the signal back to the processer the analog side is used since that is the language the processer uses satisfying the third constraint. To ensure that the Arduino does not have any current going into the I/O pins a Motor Control chip, L293D Figure 4, is there to increase the current going into the motor to make it run as well as keep the current from going in reverse bias and frying the Arduino. Using these two devices speed, rotation, and direction can be changed. The speed is dictated my the power given to each motor *This measurement will be supplied by the ME team based on constraints and parameters of the competition* 
![Elaboration Photo](../Images/Controllers/Arduino.png)
Figure 3[2]

![Elaboration Photo](../Images/Controllers/chip.png)

## **Bill of Materials:**

|Device|Quantity|Price|Total|
|-------|---|---------|-------------|
| Arduino |1|$27.60|$27.60|
| L293D |1|$8.11|$8.11|
| Soldering boards |1|$9.99|$9.99|
| | |Final Total|$45.7|

## **References:**
[1] St, https://www.st.com/content/ccc/resource/technical/document/datasheet/04/ac/22/f9/20/5d/43/a1/CD00000059.pdf/files/CD00000059.pdf/jcr:content/translations/en.CD00000059.pdf (accessed Apr. 17, 2024). 
[2] Arduino, https://docs.arduino.cc/resources/pinouts/A000066-full-pinout.pdf (accessed Apr. 17, 2024). 
[3] Arduino, https://docs.arduino.cc/resources/schematics/A000066-schematics.pdf (accessed Apr. 17, 2024). 
[4] Arduino, https://docs.arduino.cc/resources/datasheets/A000066-datasheet.pdf (accessed Apr. 17, 2024). 
[5] Admin, Technology tutorials, https://toptechboy.com/arduino-tutorial-37-understanding-how-to-control-dc-motors-in-projects/ (accessed Apr. 17, 2024). 
[6] R. Sawkare, “Arduino Uno R3 with l293d motor driver,” Medium, https://vayuyaan.medium.com/arduino-uno-r3-with-l293d-motor-driver-550c4a65f612 (accessed Apr. 17, 2024). 
