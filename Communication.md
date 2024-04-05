# Communication Subsystem

**Function:**

![Function](../Images/Communication/Conceptual.png)

Firgure 1 : Communication Subsystem

The goal of this subsystem is to recieve and transmit the data from the sensor subsystem to the processor.  

**Constraints:**

| NO. | Constraint                                                          | Origin           |
|-----|---------------------------------------------------------------------|------------------|
| 1   | The connection between the interceptor and sensors shall be a wireless connection.           |Conceptual Design |
| 2   | The wireless connection shall be protected and secured to maintain the integrity of the intercepting system                |Conceptual Design |
| 3   | The connection shall operate within the appropraite frequency ranges to meet federal requirments for free, unlicensed use             |Conceptual Design |
| 4   | The interceptor shall fit into a one-foot square on the floor and be able to fit in a one-by-one-by-one box                   |Conceptual Design|
| 5   | The wireless system needs to span over the gameboard which is 64"x78"                  |System Requirments|
| 6   | The wireless system needs to transmit the data at a high enough speed for the golf ball to be intercepted                  |System Requirments|


1. The connection between the interceptor and sensors shall be a wireless connection. [Conceptual Design]
   The communication system is establishing the connection between the sensor and the processor within the intercepting device.

2. The wireless connection shall be protected and secured to amintain the integrity of the intercepting system. [Conceptual Design]
   The connection between the sensors and processors will be password protected. The microcontroller that will be used can generate its own Wifi connection and ensure only devices with the password can use the access point. 

3. The connection shall operate within the appropraite frequency ranges to meet federal requirments for free, unlicensed use. [Conceptual Design]
   The federal government requires Wifi operation within the ranges or either 2.4 GHz or 5 GHz. The microcontroller that will be used has both Wifi and bluetooth has connection options that operate in the 2.4 GHz.

4. The interceptor shall fit into a one foot square on the floor and be able to fit in a one-by-one-by-one box. [Conceptual Design]
   The reciver of the wireless communication system will be housed in the interceptor. The size of the mircocontroller will need to be considered to stay within this constraint.

5. The wireless system needs to span over the gameboard which is 64"x78". [System Requirments]
   The range of the connection needs to be able to span over the area that the transmitting microcontroller and recieving microcontroller.

6. The wireless system needs to transmit the data at a high enough speed for the golf ball to be intercepted. [System Requirments]
   The data needs to be transmitted quickly enough for the interceptor to process the data, aim, and fire at the incoming golf ball.
