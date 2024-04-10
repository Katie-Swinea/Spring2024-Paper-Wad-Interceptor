# Battery Subsystem

## **Function:**
![Elaboration Photo](../Images/battery/BatteryPicture.png)
Figure 1: Battery Subsystem

The goal of this subsystem is to provide 5 Volt power source to power the sensor subsystem

## **Constraints:**

|No.|Constraint|Origin|
|--|------|-------|
|1|The battery shall provide a constant 5-volt power supply|Conceptual Design|
|2|Must be mounted to or from a sensor stand|Conceptual Design|
|3|Input voltage should not exceed 10-volts|Device Constraint|

## **Buildable Schematics:**
![Elaboration Photo](../Images/battery/2024-04-09.png)
Figure 2: Buildable Schematic 

## **Analyis:**
Based on the constraints given by the sensors voltage regulation and our conceptual design the team has decided to use the  AZ1117IH-5.0TRG1 chip as a voltage regulator [3]. Due to each sensor needing to have its own battery to power itself the team has decided to use a 9-volt battery for each one. However, the sensor needs a 5-volt constant power supply to fix this problem we have decided to use a linear step down voltage regulator [4] to make the voltage 5-volts. 


## **Bill of Materials:**

|Device|Quantity|Price|Total|
|-------|---|---------|-------------|
|AZ1117IH-5.0TRG1|4|$0.38|$1.52|
|Voniko 9V Batteries - Alkaline 9V Battery 4 Pack|1|$6.99|$11.35 (on sale for $6.99)|
|BATT CONN SNAP 9V 1 CEL 4" LEADS|4|$0.52|$2.08|
| | |Final Total|$14.95-$10.59|

## **References:**
[1] 232 Keystone Electronics | Battery Products | DigiKey, https://www.digikey.com/en/products/detail/keystone-electronics/232/303804 (accessed Apr. 10, 2024). 
[2] Amazon.com: Voniko 9V batteries - alkaline 9V battery 4 pack - ultra long lasting with a 7 - year shelf life : Health & Household, https://www.amazon.com/VONIKO-9V-Batteries-Alkaline-Battery/dp/B07RZ9PMQH (accessed Apr. 10, 2024). 
[3] Az1117i, https://www.diodes.com/assets/Datasheets/AZ1117I.pdf (accessed Apr. 10, 2024). 
[4] J. Teel, “How to pick the right voltage regulator(s) for your design,” PREDICTABLE DESIGNS, https://predictabledesigns.com/how-to-pick-the-right-voltage-regulators-for-your-design/ (accessed Apr. 10, 2024). 
