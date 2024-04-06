# Communication Subsystem

**Function:**

![Function](../Images/Communication/Conceptual.PNG)

Firgure 1 : Communication Subsystem

The goal of this subsystem is to recieve and transmit the data from the sensor subsystem to the processor.  

**Constraints:**

| NO. | Constraint                                                          | Origin           |
|-----|---------------------------------------------------------------------|------------------|
| 1   | The connection between the interceptor and sensors shall be a wireless connection.           |Conceptual Design |
| 2   | The wireless connection shall be protected and secured to maintain the integrity of the intercepting system                |Conceptual Design |
| 3   | The connection shall operate within the appropraite frequency ranges to meet federal requirments for free, unlicensed use             |Conceptual Design |
| 4   | The interceptor shall fit into a one-foot square on the floor and be able to fit in a one-by-one-by-one box                   |Conceptual Design|
| 5   | The wireless connection needs to transmit data fast enough for the interceptor to deflect the golf ball                   |Conceptual Design|
| 6   | The wireless system needs to span over the gameboard which is 64"x78"                  |System Requirments|
| 7   | The wireless system needs to transmit the data at a high enough speed for the golf ball to be intercepted                  |System Requirments|
| 8   | The wireless system needs to have pin connections that allow it to connect with the sensor                 |System Requirments|
| 9   | The transmitter and reciever used for the wireless connection will need 3.3 volts for operation                 |Device Constraint|

1. The connection between the interceptor and sensors shall be a wireless connection. [Conceptual Design]
   The communication system is establishing the connection between the sensor and the processor within the intercepting device.

2. The wireless connection shall be protected and secured to amintain the integrity of the intercepting system. [Conceptual Design]
   The connection between the sensors and processors will be password protected. The microcontroller that will be used can generate its own Wifi connection and ensure only devices with the password can use the access point. 

3. The connection shall operate within the appropraite frequency ranges to meet federal requirments for free, unlicensed use. [Conceptual Design]
   The federal government requires Wifi operation within the ranges or either 2.4 GHz or 5 GHz. The microcontroller that will be used has both Wifi and bluetooth has connection options that operate in the 2.4 GHz.

4. The interceptor shall fit into a one foot square on the floor and be able to fit in a one-by-one-by-one box. [Conceptual Design]
   The reciver of the wireless communication system will be housed in the interceptor. The size of the mircocontroller will need to be considered to stay within this constraint.

5. The wireless connection needs to transmit data fast enough for the interceptor to deflect the golf ball. [Conceptual Design]
   If the data takes too long to be transmitted, the incoming golf ball will not be intercepted in time. The calculation made in the conceptual design determines that the connection speed needs to be at least 10.3 Mbps. The equipment used will be capable of reaching speeds this high.

6. The wireless system needs to span over the gameboard which is 64"x78". [System Requirments]
   The range of the connection needs to be able to span over the area that the transmitting microcontroller and recieving microcontroller.

7. The wireless system needs to transmit the data at a high enough speed for the golf ball to be intercepted. [System Requirments]
   The data needs to be transmitted quickly enough for the interceptor to process the data, aim, and fire at the incoming golf ball.
   
8. The wireless system needs to have pin connections that allow it to connect with the sensor. [System Requirments]
   The data from the sensor uses either an I2C or SPI protocol to send the recieved data to a microcontroller. The microcontroller that will be needs to have pin connections to support these protcols and recieve the data.

9. The transmitter and reciever used for the wireless connection will need 3.3 volts for operation. [Device Constraint]
   The ESP-WROOM-32 microcontroller fulfills the constraints imposed by the stakeholders and the requirments of the other designs of the system. This device requires 3.3 volts for operation. This microcontroller will act as the reciever and transmitter since it is capable of creating its own Wifi network.

**Analysis:**

Based on the constraints given, the team chose the ESP_WROOM-32. This was chosen because of the wireless communication capablities and the support of both communication forms of the VL53L8CX sensor. Another reason this model was chosen is the ability to directly communicate with both the sensor and processor via pin connections while also being able to establish a wireless connection between two of the microcontrollers. The specific board chosen was the ESP32 DevKitC V4. This is simple and includes all the pin connections for the specific chip being used. It also offers extra power supply options with a USB port and a 5 volt input pin. The exact specification and advantages of this choice will be further discussed.

