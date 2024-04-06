# Emergency Stop and Pause

![System](../Images/EstopandPause/E-StopPauseImage.png)
Figure 1: Emergency Stop and Pause sub-system, seen here as the color red.

- The goal of this subsystem is to adhere to the rules as provided by the customer, Devcom. The system needs a pause switch to deactivate it between rounds and the emergency stop will be used to deenergize the system.

## **Constraints:**

| **Number:** | **Constraint:** | **Origin:** | 
| --- | --- | --- |
| 1. | The interceptor needs to have an E-stop that deenergizes the interceptor. | Rulebook |
| 2. | The interceptor needs a switch that sets the system into a pause state.  | Rulebook |
| 3. | --- | --- |
| 4. | --- | --- |

1. One of the requirements in the rulebook, given to us by the customer, is that the interceptor needs to have an emergency stop that deenergizes the interceptor. This will be needed to ensure that the design passes the safety check.
   
2. One of the requirements in the rulebook, given to us by the customer, is that the interceptor needs to have a pause switch that keeps the interceptor from firing when the board is being reset. This switch will need to be physical, but in the implementation, it will run to the processor where it will prevent it from outputting any signals.
   
3.

## **Analysis**
For the pause switch component, there are many different switches that can be chosen. Switches range between single pole single throw and upwards. The switch that needs to be implemented for the pause switch should be a single pole single throw switch that has a single on and off function. This will ensure that with one connection the processor will be receiving 5V, which will count as a binary one, and when the switch is off the processor will not be connected which will be interpreted as a binary zero. The switch that was chosen for this task is the NTE Electronics, 54-571. This switch is rated for 20A and 12VDC which will be more than enough for this simple task. The other main portion of the pause switch is the implementation in the code of the processor. Because a processor has not been chosen now it is not possible to say exactly how this will be implemented, but pseudocode can be written to make the coding process easier. To be clear when the pause switch is on 5V or equivalent will be allowed to pass and when it is off the circuit will not be connected. This input will be interpreted as a variable and when the circuit is on the processor will be allowed to collect the data from the sensors. When the switch is off the processor will be in the pause state where it can not do anything but wait for the switch to be turned on.



## Bill of Materials

| **Items:** | **Quantity:** | **Price:** | **Total:** |
| --- | --- | --- | --- |
| NTE Electronics, 54-571 | 1 | $3.48 | $3.48 |

