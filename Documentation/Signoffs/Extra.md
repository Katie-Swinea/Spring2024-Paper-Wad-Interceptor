# Extra

![System](../Images/Extra_jrneal20.png)

Figure 1: Extra subsystem and the pause switch can be seen in this figure.

- The goal of this subsystem is to adhere to the rules as provided by the customer, Devcom, and to add lights and sounds to the design which will add to the point total as provided by Devcom. The system needs a pause switch to deactivate it between rounds. The system will also include lights and sounds before launching a projectile to add to the decoration portion of the design.
## **Constraints:**

| **Number:** | **Constraint:** | **Origin:** | 
| --- | --- | --- |
| 1. |  The interceptor shall have a switch that sets the system into a pause state that will keep the interceptor from firing. | Rulebook |
| 2. | The voltage switched by the pause switch shall be 5V. | System Constraint|
| 3. | | |

1. One of the requirements in the rulebook, given to us by the customer, is that the interceptor needs to have an emergency stop that de-energizes the interceptor. This emergency stop will cut power off the device power system that will de-energize all of the systems that are being powered by the device power system. This functionality will be needed to ensure that the design passes the safety check.
   
2. One of the requirements in the rulebook, given to us by the customer, is that the interceptor needs to have a pause switch that keeps the interceptor from firing when the board is being reset. This switch will need to be physical, but in the implementation, it will run to the processor where it will prevent it from outputting any signals. When the switch is engaged it will keep the processor block from outputting signals to the mechanical system. This will ensure that the interceptor does not fire while the judges are in the competition area.
   
3. The circuit that is implemented by the pause switch needs to fall within the limitations of the processor block. Based on the processors that could be chosen the voltage that will be switched will be 5V.
## Buildable Schematic
![System](../Images/Switch_Buildable_2.png)

Figure 2: The 5V source will most likely come from an output of the processor block but if this is not possible it may have to come from the power block. Either way, the switch will go into the processor block. 


![System](../Images/E-Stop_Buildable.png)

Figure 3: The image shows the connections of the Prime extension cord and the connections that will be made. The circle in the middle represents the foot switch which includes the LEDs to indicate if the power is on or off. 

## **Analysis**
For the pause switch component, there are many different switches that can be chosen. Switches range between single pole single throw and upwards. The switch that needs to be implemented for the pause switch should be a single pole double-throw switch that has a two on functions and an off function. This will ensure that with one connection the processor will be receiving 5V, which will count as a binary one, and when the switch is off the processor will be connected to ground which will be interpreted as a binary zero. The switch that was chosen for this task is the NTE Electronics, 54-571-2 [1]. This switch is rated for 20A and 12VDC which will be more than enough for this simple task. The other main portion of the pause switch is the implementation in the code of the processor. Because a processor has not been chosen now it is not possible to say exactly how this will be implemented, but pseudocode can be written to make the coding process easier. To be clear when the pause switch is on 5V or equivalent will be allowed to pass and when it is off the circuit will not be connected. This input will be interpreted as a variable and when the circuit is on the processor will be allowed to collect the data from the sensors. When the switch is off the processor will be in the pause state where it can not do anything but wait for the switch to be turned on.

The emergency stop is a constraint that was added by the customer, Devcom. This switch has one purpose and that is to de-energize the system. The thought was this could easily be done by cutting off the power directly at the source. This can be done with the PRIME 3-Outlet Extension Cord with Lighted Footswitch [2]. This extension cord is rated for 13A and 125V which will be more than enough for the power that needs to be supplied to the power subsystem. This is the typical output for a wall outlet in the United States. The power subsystem is made up of two AC to DC converters. The first one is a converter for the mechanical subsystem, which is 24V and 2A or 48W, and the second is for the processor and communication system, which is 12V and 2A or 24W. The main selling point of this item is that it includes two LEDs that indicate when the power is on and off. Based on the description the foot switch displays red when the power is off and green when the power is on. This will be perfect for the team’s application because it will be very easy to identify when the power is on and off. 


## Bill of Materials

| **Items:** | **Quantity:** | **Price:** | **Total:** |
| --- | --- | --- | --- |
| NTE Electronics, 54-571 | 1 | $3.48 | $3.48 |
| PRIME Extension Cord | 1 | $6.98 | $10.46 |

## References
1. [1] “Toggle switches,” NTE Electronics, https://www.nteinc.com/switches/pdf/toggle-std.pdf (accessed Apr. 6, 2024).

2. [2] “9FT 16/2 SPT-2 Green 3-Outlet Extension Cord W/Lighted Footswitch,” Prime Wire & Cable Inc., https://primewirecable.com/products/fsl7806099ft-16-2-spt-2-green-3-outlet-extension-cord-w-lighted-footswitch?_pos=1&_sid=f6715f7aa&_ss=r (accessed Apr. 6, 2024). 
‌