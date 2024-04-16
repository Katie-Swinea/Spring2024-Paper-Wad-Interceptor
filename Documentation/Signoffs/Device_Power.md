# Device Power Subsystem

**Function:**

![Function](../Images/Device_Power/Conceptual2.png)

Figure 1: Device Power Subsystem

The goal of this subsystem is to convert AC power from the wall outlet to DC power, and then distribute that power to the different device systems.  

**Constraints:**

| NO. | Constraint                                                          | Origin           |
|-----|---------------------------------------------------------------------|------------------|
| 1   | The power system shall be controlled by an emergency stop which will de-energize the device power system that will in turn de-energize the interceptor itself. This will only be used if the system threatens peoples safety |Conceptual Design |
| 2   | The system shall convert 100-120 wall outlet AC voltage to 60, which is required by the main/processor unit and extra subsystem, and 48 Watts DC, which is required by the mechanical unit |Conceptual Design |
| 3   | The system shall provide a minimum of 72.6 Watts (1.2 times the minimum wattage)     |Design Constraint |
| 4   | The system shall be controlled by a power switch                 |Conceptual Design |
| 5   | The system shall be able to step down the power supply voltage to 5 volts, to power the main/processor unit, and 9 volts, to power the extra unit, respectively |Design Constraint |
| 6   | The system shall be able to produce 24 volts to power the mechanical unit (required voltage of that unit)    |Design Constraint |



<sup>1</sup> The power system shall be controlled by an emergency stop which will de-energizes the device power system that will in turn de-energize the interceptor itself. [Conceptual Design]

One of the requirements in the rulebook, given to us by the customer, is that the interceptor needs to have an emergency stop that de-energizes the interceptor. This emergency stop will cut power from the wall outlet to the AC-DC convertors which will de-energize all of the systems that are being powered by this power system. This system will only be used as a last case option if the interceptor threatens peoples safety. 

<sup>2</sup> The system shall convert 100-120 wall outlet AC voltage to 60, which is required by the main/processor unit and extra subsystem, and 48 Watts DC, which is required by the mechanical unit [Conceptual Design]

This system will take the 100-120 AC voltage supplied from the wall outlet and then convert that to 2 DC power signals that will be provided to the other subsystems. These DC signals are 60 Watts to the main/processor and communication receiver and 48 Watts to the mechanical unit.

<sup>3</sup> The system shall provide a minimum of 72.6 Watts (1.2 times the minimum wattage) [Design Constraint]

Due to possible overclocking and power spikes, this system will provide 1.2 times the required wattage [1]. Because of this, the system will provide 72.16 watts of power, which is over 1.2 times the required wattage. This is shown in the below table:

| System | Required Voltage | Required Current | Required Power |
|--------|------------------|------------------|----------------|
| Mechanical | 24 Volts | 1.5 Amps | 36 Watts |
| Extras | 9 Volts | 0.5 Amps | 4.5 Watts |
| Processor | 5 Volts | 4 Amps | 20 Watts |
| Total | ---- | ---- | 60.5 Watts |


72.16 Watts of power is 1.2 times the required total wattage of this system. This system will use AC-DC convertors that will supply a total of 108 watts of power which will be well over the 1.2 requirement. 

<sup>4</sup>  The system shall be controlled by a power switch  [Conceptual Design]

The system will be controlled by an on/off switch. This switch will allow the wall power to be connected or disconnected from each system that this subsystem powers.  

<sup>5</sup> The system shall be able to step down the power supply voltage to 5 volts, to power the main/processor unit, and 9 volts, to power the extra unit, respectively [Design Constraint]

The main/processor unit requires a voltage input of 5 volts. This system must be able to take the power supply voltage from the AC to DC convertor and step it down to 5 volts to power this unit. 

The communication receiver requires a voltage input of 9 volts. This system must be able to take the power supply voltage from the AC to DC convertor and step it down to 9 volts to power this unit. 

<sup>6</sup> The system shall be able to produce 24 volts to power the mechanical unit  [Design Constraint]

The mechanical unit requires a voltage input of 24 volts. This system must be able to produce the 24 V DC signal from the wall outlet.

## Buildable schematic 

![Function](../Images/Device_Power/kicad4.png)

*power subsystem buildable schematic*

## Analysis

| System        | Voltage    | Current   | Power       | 
|---------------|------------|-----------|-------------|
| mechanical    | 24 Volts   | 1.5 Amps  | 36 Watts    |
| Communication | 9 Volts  | 500 mAmps | 4.5 Watts  |
| Processor     | 5 Volts    | 4 Amps    | 20 Watts    |
| Total         | 38 | 6    | 60.5 Watts |

The above table details the different power draws that is required from this system. 

Mechanical:

The mechanical unit requires 24 volts and 1.5 amps. This means the total power needed will be:

~~~ math

(24 Volts) * (1.5 Amps) = 36 Watts

~~~

Communication:

The communication unit requires 9 volts and 500 mAmps. This means the total power needed will be:

~~~math

(9 Volts) * (500 mAmps) = 4.5 Watts

~~~

Processor:

The processor unit requires 5 Volts and 4 Amps. This means the total power needed will be:

~~~math

(5 Volts) * (4 Amps) = 15 Watts

~~~

Total subsystem power:

The total power of the entire subsystem will be:

~~~math

(36 Watts) + (4.5 Watts) + (20 Watts) = 60.5 Watts

~~~



## Fulfilling Constraints

This switch has one purpose and that is to de-energize the system. This can easily be done by cutting off the power directly at the source. This will be accomplished with the Power Strip Surge Protector 2-Pack - 4 Outlets & 2 Ft Extension Cord, 1875W/15A 90 Joules [9]. This extension cord is rated for 1875 Watts. This will have a high enough power rating as this system will only be drawing up to 108 Watts. <sup>1</sup>

The system must convert AC power from the wall outlet and output a DC signal. This system will use two separate AC to DC converters. The first will produce a signal of 12 volts/ 5 amps (60 watts). This converter will power the two step-down transformers. The transformer will be the Chanzon 12V 5A LED Strip Power Supply 60W AC DC Adapter UL Listed for CCTV 2.1x5.5 2.5x5.5 Plug  [5]. The second will produce a signal of 24 volts/ 2 amps (48 watts). This converter will power the mechanical unit. The transformer will be the AC to DC 24V 2A Power Supply Adapter, Plug 5.5mm x 2.1mm UL Listed FCC [7]. <sup>2</sup>

The system must provide a total of 72.6 watts. This is because the total wattage of each system added together will be 60.5 watts:

~~~math
Total System Power: (36 Watts) + (4.5 Watts) + (20 Watts) = 60.5 Watts
~~~

As stated above, the system will provide at least 1.2 times the amount of required power. This is why the system will need to provide 72.16 watts total. This will be done through two converters. The first will output a total of 60 watts. The systems it will support are the processor and extra systems, which require 24.5 watts. 60 watts is over 1.2 times that amount. The second will produce 48 watts. The system it supports requires 36 watts. 48 watts is over 1.2 times that amount. <sup>3</sup>

This system will have a power switch connected between the AC-DC transformers and there adjacent outputs. Both converters will controlled using the KRE2ANA1BBD switch rocker [6]. This switch is rated for a max of 28 volts/ 6 amps. These ratings will completely encapsulate the requirements for each convertor. <sup>4</sup>

The system must supply 5 volts/ 4 amps, and 9 volts/ 0.5 amp respectively. This will be accomplished by steping down the 12 volt/ 2 amp convertor in two different intervals. To supply 5 volts/ 4 amps the system will use the DC-DC 24V 12V to 5V 4A (max) 20W Converter DC Step-Down Voltage Regulator Waterproof Step-Down Module which takes a 12 volt input and outputs a 5 volt/ 4 amps signal [2]. To supply 9 volts / 0.5 amp the system will use the 12V to 9V 1.7A Step-Down Waterproof Miniature DC-DC Converter Power Supply which takes 12 volts and outputs a 9 volt 1.7 amp signal [3]. This will work for the system as the arduino will only draw the current that it needs and no more. <sup>5</sup>

The system must supply a 24 volt/ 1.5 amp signal for the mechanical unit. This will be done using the AC to DC 24V 2A Power Supply Adapter, Plug 5.5mm x 2.1mm UL Listed FCC, as it produces a 24 volt/ 2 amp output [7]. <sup>6</sup>

## Application

To connect each system, there will be 2 soldered breadboards. One will connect the 12 volt convertor to the power switch and then connect that output to both of the step-down converters. The output of those will be connected to their actual systems using DC jack connector plugs [10]. The second will connect the 24 volt converter to the switch and then connect the output of that switch to the actual system. The board that will be used will be a double-sided ENIG Protoboard [8].

There are also plans to 3d print a box to encapsulate each power system's components if time permits. 

## BOM

|Device     | Quantity | Price per  | Total price  |
|-----------|----------|------------|--------------|
|Chanzon 12 v to 5 v power supply | 1 | 17.99 | 17.99 |
|Double Sided ENIG Protoboard | 2 | 3.59 | 7.18 |
|12 v to 5 v/ 4 amp convertor | 1 | 18.99 | 18.99 |
|12V to 9V 1.7A Step-Down | 1 | 6.89 | 6.89 |
| 20 Pcs DC Power Cable 5A 12v DC Power Plug Cord Male Connectors 2.1mm x 5.5mm | 1 | 9.59 | 9.59 |
|Power Strip Surge Protector 2-Pack - 4 Outlets & 2 Ft Extension Cord | 1 | 9.99 | 9.99 |
|AC to DC 24V 2A Power Supply Adapter | 1 | 9.99 | 9.99 |
|KRE2ANA1BBD | 2 | 3.20 | 6.40 |
|Total | 10 | --- | 87.02 |

## References 

[1] “How do you balance performance, reliability, and cost when installing a power supply?,” How to Install a Power Supply: Tips on Wattage, Efficiency, and Quality, https://www.linkedin.com/advice/0/how-do-you-balance-performance-reliability (accessed Apr. 7, 2024). 

[2] “Amazon.com: Waterproof voltage power AC 12V 24V to DC 5V Buck Voltage Regulator Waterproof Power Module for car waterproof step down converter (1A) : Beauty & Personal Care,” Amazon, https://www.amazon.com/Waterproof-Voltage-Regulator-Module-Converter/dp/B07TLLB35X (accessed Apr. 16, 2024). 

[3] Amazon.com: 12V to 9V 1.7a step-down waterproof miniature DC-DC converter power supply module by Envistia Mall : Electronics, https://www.amazon.com/9V-1-7A-DC-DC-Converter-Envistia/dp/B07QGXL9XP (accessed Apr. 16, 2024). 

[4] 3.0 A, step-down switching regulator LM2596, https://www.onsemi.com/pdf/datasheet/lm2596-d.pdf (accessed Apr. 8, 2024). 

[5] “Chanzon 12V 5A led Strip Power Supply 60W AC DC adapter UL listed for CCTV 2.1x5.5 2.5x5.5 plug (input 110V-220V, output 12 volt 5 AMP 60 watt) converter led driver lighting Transformer 12 V 5 A - amazon.com,” Amazon, https://www.amazon.com/110V-220V-Converter-Lighting-Transformer-Flexible/dp/B073QTNF9F (accessed Apr. 16, 2024). 

[6] ZF, http://switches-sensors.zf.com/us/wp-content/uploads/sites/7/2012/10/Rocker_KR_Datasheet_08-11-17.pdf (accessed Apr. 8, 2024). 

[7] “AC to DC 24V 2A Power Supply Adapter, Plug 5.5mm x 2.1mm UL Listed FCC,” Amazon, https://www.amazon.com/Power-Supply-Adapter-5-5mm-Listed/dp/B08T636YVR/ref=asc_df_B08T636YVR/?tag=hyprod-20&linkCode=df0&hvadid=507792222889&hvpos=&hvnetw=g&hvrand=12806499727394812437&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=1025954&hvtargid=pla-1262398291870&psc=1&mcid=edd9d085cf3b3cc6915cbdb81a548b03&gclid=Cj0KCQjwq86wBhDiARIsAJhuphlXeLT83NoSYTl9ESdo2cRMDwrTjeLdDQEmibtQ-LtuMLKLdhcwaioaAohBEALw_wcB (accessed Apr. 8, 2024). 

[8] “Schmalztech premium solderless breadboard/Electronics Prototyping Bread Board for quick circuit building, Arduino, or Raspberry Pi, st-BB (470 position): Amazon.com: Industrial & Scientific,” Amazon, https://www.amazon.com/SchmalzTech-Solderless-Breadboard-Electronics-Prototyping/dp/B0C3YZRMR5 (accessed Apr. 8, 2024). 

[9] “Amazon.com: Plugtul Power Strip Surge protector 2-pack - 4 outlets & 2 ft extension cord, 1875W/15A 90 joules, Overload & Surge Protection, wall mount for home office, ETL listed White : Electronics,” Amazon, https://www.amazon.com/PLUGTUL-Power-Strip-Protector-2-Pack/dp/B0BP2HJJTK (accessed Apr. 16, 2024). ‌

[10] Amazon, https://www.amazon.com/dp/B0BTHSDF4S/ref=sspa_dk_detail_1?pd_rd_i=B0BTHRYSDX&pd_rd_w=hEv4T&content-id=amzn1.sym.386c274b-4bfe-4421-9052-a1a56db557ab&pf_rd_p=386c274b-4bfe-4421-9052-a1a56db557ab&pf_rd_r=ZRBWFE7QM0A3Z2BGD3RQ&pd_rd_wg=E86ve&pd_rd_r=a270ba38-3242-4719-bd84-0cc3408e87f7&s=electronics&sp_csd=d2lkZ2V0TmFtZT1zcF9kZXRhaWxfdGhlbWF0aWM&th=1 (accessed Apr. 15, 2024).  
