# Device Power Subsystem

**Function:**

![Function](../Images/Device_Power/Conceptual2.png)

Firgure 1 : Device Power Subsystem

The goal of this subsystem is to convert AC power from the wall outlet to DC power, then distribute that power to the different device systems.  

**Constraints:**

| NO. | Constraint                                                          | Origin           |
|-----|---------------------------------------------------------------------|------------------|
| 1   | The power system shall be connected to the emergancy stop           |Conceptual Design |
| 2   | The power system shall power the main/processor unit                |Conceptual Design |
| 3   | The power system shall power the communication receiver             |Conceptual Design |
| 4   | The power system shall power the mechanical unit                    |Conceptual Design |
| 5   | The system shall convert AC power to DC power                       |Conceptual Design |
| 6   | The system shall provide a minimum of 85 Watts                         |Design Constraint |
| 7   | The system shall have a connected power switch                      |Conceptual Design |
| 8   | The system shall be able to step down voltage to 5 v and 3.3 v respectively |Design Constraint |
| 9   | The system shall be able to step up voltage to 30 v                  |Design Constraint |



<sup>1</sup> The power system shall be connected to the emergancy stop [Conceptual Design]

The power system will be connected to the emergancy stop which will act as an extension cord with a turn of switch. This emergancy stop will be directly connected to the wall outlet.

<sup>2</sup> The power system shall power the main/processor unit [Conceptual Design]

The system will need to be the primary power source for the main/processor unit. This system will be responsible for powering or providing the necessary power to every componet in the main unit. 

<sup>3</sup> The power system shall power the communication receiver [Conceptual Design]

The system will need to be the primary power source for the communication unit. This system will be responsible for powering or providing the necessary power to every componet in the communication unit. 

<sup>4</sup> The power system shall power the mechanical unit [Conceptual Design]

The system will need to be the primary power source for the mechanical unit. This system will be responsible for powering or providing the necessary power to every componet in the mechanical unit. 

<sup>5</sup> The system shall convert AC power to DC power [Conceptual Design]

This system will take the AC power supplied from the wall outlet and then convert that to a DC signal that will be provided to the other subsystems. 

<sup>6</sup> The system shall provide a minimum 59.196 W [Design Constraint]

Due to possible overclocking and power spikes this system will provide 1.2 times the required wattage. [1] Becuase of this, the system will provide 85 watts of power, which is over 1.2 times the required wattage (70.65 watts). This will ensure there is plenty of power for the entire system. 

<sup>7</sup>  The system shall have a connected power switch [Conceptual Design]

The system will be controlled by an on/off switch. This switch will allow the wall power to be connected or disconnected from each system that this subsystem powers.  

<sup>8</sup> The system shall be able to step down voltage to 5 v and 3.3 v respectively [Design Constraint]

The main/processor unit requires a voltage input of 5 v. This system must be able to step down the DC voltage acquired by the wall outlet to 5 v to power this unit. 

The communication receiver requires a voltage input of 3.3 v. This system must be able to step down the DC voltage acquired by the wall outlet to 3.3 v to power this unit. 

<sup>9</sup> The system shall be able to step up voltage to 30 v [Design Constraint]

The mechanical unit requires a voltage input of 30 v. This system must be able to step up the DC voltage acquired by the wall outlet to 30 v to power this unit.



## Analysis

| System        | Voltage    | Current   | Power       | 
|---------------|------------|-----------|-------------|
| Mechincial    | 30 Volts   | 1.5 Amps  | 45 Watts    |
| Communication | 3.3 Volts  | 500 mAmps | 1.65 Watts  |
| Processor     | 5 Volts    | 3 Amps    | 15 Watts    |
| Total         | 38.3 Volts | 5 Amps    | 70.65 Watts |


## Fulfilling Constraints

As the schematic depicts this subsystem is connected to the emergancy stop subsystem. The emergancy stop subsystem is connected to the wall outlet. This allows the power subsystem to be disconnected from power completely if needed. <sup>1</sup>

The main/processor unit requires a 5 volt/ 3 amp input (15 Watts). The 12V to 5V DC USB Type-C Right Angle Step-Down Power Converter takes a 12 volt input and outputs a 5 volt/ 3 amp signal. [2] This is exactly what the wall outlet transformer produces and it is exactly what the main/processor requires. <sup>2</sup>

The communication receiver requires a 3.3 volt/ 0.5 amp (or more) input (1.65 Watts). The LM2596 takes a 12 volt input and can convert a 3.3 volt output with a 1 amp, 1.5 amp, or 2 amp signal.[3] This system will output a 3.3 volt/ 1 amp output. This will be sufficient as the wall outlet transformer produces 12 volts and it encapsulates what is required by the communication receiver. <sup>3</sup>




The system must convert AC power from the wall outlet and output a DC signal. This system will use the Chanzon 12V 3A UL Listed 36W AC DC Switching Power Supply Adapter Wal Wart, which will take the AC power signal from the outlet and output a 12 volt/ 3 amp signal. [6] This is an appropriate signal becuase all step up and step down transformers that will be used in this system require a 12 volt input and need to output at least 3 amps. This convertor will allow both of these specifications to be possible. <sup>5</sup>








## References 

[1] “How do you balance performance, reliability, and cost when installing a power supply?,” How to Install a Power Supply: Tips on Wattage, Efficiency, and Quality, https://www.linkedin.com/advice/0/how-do-you-balance-performance-reliability (accessed Apr. 7, 2024). 

[2] “12V to 5V DC USB Type-C Right Angle Step-Down Power Converter, Buck Converter, 15W Output, 3A at 5V USB Type-C Power Supply, Waterproof (12V to 5V USB-C Power Converter),” Amazon, 12V to 5V DC USB Type-C Right Angle Step-Down Power Converter, Buck Converter, 15W Output, 3A at 5V USB Type-C Power Supply, Waterproof (12V to 5V USB-C Power Converter) (accessed Apr. 7, 2024). 

[3] “LM2596S adjustable DC-DC step-down module,” ProtoSupplies, https://protosupplies.com/product/lm2596s-adjustable-dc-dc-step-down-module/ (accessed Apr. 7, 2024). 

[4] 3.0 A, step-down switching regulator LM2596, https://www.onsemi.com/pdf/datasheet/lm2596-d.pdf (accessed Apr. 8, 2024). 

[5] Amazon.com: 10Gtek# Buck Converter step Down Module LM2596 DC to DC voltage regulator, 3.0~40V to 1.5~35V Power Supply Module, pack of 2 : Automotive, https://www.amazon.com/10Gtek-Step-Down-Buck-Converter/dp/B0CBM7NKCF (accessed Apr. 8, 2024). 

[6] “Chanzon 12V 3A UL Listed 36W AC DC Switching Power Supply Adapter,” Amazon, https://www.amazon.com/Chanzon-Switching-Adapter-100-240V-Transformer/dp/B07HNV6SBJ/ref=asc_df_B07HNV6SBJ/?tag=hyprod-20&linkCode=df0&hvadid=642112814556&hvpos=&hvnetw=g&hvrand=17615749528492740576&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=1025954&hvtargid=pla-2003424733647&psc=1&mcid=4736db59cf7d3c128d37e2796e082608 (accessed Apr. 7, 2024). 
