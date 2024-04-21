# Extra

![System](../Images/Extra_jrneal20.png)

Figure 1: Extra subsystem and the pause switch can be seen in this figure.

- The goal of this subsystem is to adhere to the rules as provided by the customer, Devcom, and to add lights and sounds to the design which will add to the point total as provided by Devcom. The system needs a pause switch to deactivate it between rounds. The system will also include lights and sounds before launching a projectile to add to the decoration portion of the design.

## **Constraints:**

| **Number:** | **Constraint:** | **Origin:** | 
| --- | --- | --- |
| 1. |  The interceptor shall have a switch that sets the system into a pause state that will keep the interceptor from firing. | Rulebook |
| 2. | The voltage switched by the pause switch shall be 5V. | System Constraint|
| 3. | The interceptor must have lights that are bright enough to be seen by the judges. These lights must be powered by a 5V source from the processor block and must emit a light that falls within the visual light spectrum of 380 to 720 nanometers [1].  | Rulebook / System |
| 4. | The interceptor must make sounds before firing. The sounds will be powered by a voltage of 5V and the sounds will need to fall within the range of frequency humans can hear which is 20 to 20,000Hz [2]. The volume, or loudness, must fall within a range of 0, the threshold, to a maximum of 120dB and must not exceed 85dB for more than eight hours or it may cause hearing damage [2]. The buzzer should be louder than average room noise which is 30-50 dB [2]. | Rulebook / Safety |
   
1. One of the requirements in the rulebook, given to us by the customer, is that the interceptor needs to have a pause switch that keeps the interceptor from firing when the board is being reset. This switch will need to be physical, but in the implementation, it will run to the processor where it will prevent it from outputting any signals. When the switch is engaged it will keep the processor block from outputting signals to the mechanical system. This will ensure that the interceptor does not fire while the judges are in the competition area.
   
2. The circuit that is implemented by the pause switch needs to fall within the limitations of the processor block. Based on the processors that could be chosen the voltage that will be switched will be 5V. This source will be connected to a PCB that will be connecting the circuit components.

3. To add to the total points for the competition, the interceptor must have lights. This constraint can be found in the official rulebook for the competition. Any amount of visual light, which falls within 380 to 720 nanometers [1], is sufficient to count for the constraint. Therefore two arrays of ten LED's will be used for this. These LED's must be able to be powered by a 5V source that comes from the processor block. These LED’s emit light with a wavelength of 565nm for the green LED and 617nm for the red LED. This is with 10mA of current and in the current setup 20mA are being supplied which is more than enough to show these lights will be visible.
   
5. To add to the total points for the competition, the interceptor must make sounds before firing. This constraint can be found in the official rulebook for the competition. The piezo buzzer must be able to work with an output of the Arduino Uno R3 which will be 5V. It must also fall within the human hearing range of frequency which is 20 to approximately 20,000Hz. The piezo buzzer that was chosen operates at a frequency of 3600Hz to 4600Hz which will fall within the frequency range that we can hear. When it comes to loudness, humans can tolerate a range of 0 to 120db and the sound must not exceed 85db for long periods which will keep the noise at a save level [2]. The buzzer that has been chosen operates from 3 to 16 VDC and operates at a minimum of 70db at 12V therefore at the voltage that is being used, the sounds will be at a safe level for the small periods of time that they will be used. 
   
## Buildable Schematic
![System](../Images/Extra-Buildable_Pause_Switch.png)

Figure 1: This represents the buildable schematic for the pause switch. This switch outputs 5V or ground that is sent to the processor block and the LED array. The 5V and ground will both come from the processor block. In this example, the red LED's will be at the top, and the green LED's will be at the bottom.

![System](../Images/Buildable_Buzzer.png)

Figure 2: This image shows the buildable schematic for the buzzer system. This buzzer is powered by an Arduino Uno R3 that takes a power input from the device power system of 9V and an input from the processor to tell the arduino when to play the sounds. Finally, it outputs 5V for the buzzer to play the sound.


## **Analysis**
For the pause switch component, there are many different switches that can be chosen. Switches range between single pole single throw and upwards. The switch that needs to be implemented for the pause switch should be a single pole double-throw switch that has a two on functions and an off function. This will ensure that with one connection the processor will be receiving 5V, which will count as a binary one, and when the switch is off the processor will be connected to ground which will be interpreted as a binary zero. 5V has been chosen as the voltage because all of the processors that will possibly be chosen have a 5V output. The switch that was chosen for this task is the CIT Relay and Switch, ANT11SF1CQE [3]. This switch is rated for 5A and 28VDC which will be more than enough for this simple task. The other main portion of the pause switch is the implementation in the code of the processor. Because a processor has not been chosen now it is not possible to say exactly how this will be implemented, but pseudocode can be written to make the coding process easier. To be clear when the pause switch is on 5V or equivalent will be allowed to pass and when it is off the circuit will not be connected. This input will be interpreted as a variable and when the circuit is on the processor will be allowed to collect the data from the sensors. When the switch is off the processor will be in the pause state where it can not do anything but wait for the switch to be turned on. 

When the output of the switch is connected to 5V this will be sent to the processor and an array of ten red LED's with a light of 624nm [4] and ten current limiting resistors that will indicate that the interceptor has been put into pause mode. This set of LED's will be connected to the processor node on one side and the gound on the other. This will allow current to flow when the switch is connected to 5V. The array of ten green LED's with a light of 525nm [5] will be connected to the processor node on one side and 5V on the other. When the switch is connected to the ground current will flow from the 5V to the ground which will light up the green LED's. This will serve to show that the interceptor is in the pause state.

![System](../Images/Led_Equation.png) [6]

The maximum current that can be handled by the LED's is 30mA for the green LED's and for the red it is 50mA. Because of the 5V being used a resistor value was chosen, using the equation above [6], to keep the LED's below their maximum ratings. Both resistors share the same Vs of 5V. The values for the red LED were found using the datasheet those values are: Vf = max of 3.0V and If DC = max of 50mA [7]. For the green LED's the datasheet was used to find values of Vf = 3.6V max and If DC = 30mA max [8]. These values were then put into the equation above [6] and resistance values were calculated to make both resistors. The green LED's need a resistance of 75 Ohm [9] and the red LED's need a resistance of 50 Ohm [10]. For the green LED this sets the voltage at 3.5V and the current at 20mA. This allows for the light intensity to be calculated from the datasheet, at 20mA the LED is rated for 25cd [8]. For the red LED, the values are set at 2.5V and 50mA. Based on the datasheet, a current of 50mA produces a value of 25cd [7]. This sets the power consumtion at 0.125W for the red LED and 0.03W for the green LED, according to the equation below. 

$$P=IV$$

The interceptor sound controller will be an Arduino Uno r3 [7] and it will be making a sound using a piezo buzzer. The Arduino r3 was chosen because of its ease of use and the availability of open-source code and documentation. The schematic can be seen in figure two. The wiring diagram is very simple and only involves a few connections. The first connection would be from the GPIO (General Purpose Input Output) pins to the positive connection of the buzzer and then the ground would be connected to the ground of the board. All that would be left is the code for making the sounds. The code written would need to generate a sound that is tolerable and falls within the frequency requirements of the piezo buzzer. This sound would be played for a defined period of time when the processor sends the proper signal. The buzzer that was chosen is the KINGSTATE KPEG242 [8]. This buzzer is rated for 3V to 16V DC and a frequency of 3600Hz to 4600Hz. This means that the output of the Arduino should not exceed 16V and 4600Hz to ensure that the buzzer is operating properly. 


## Bill of Materials

| **Items:** | **Quantity:** | **Price:** | **Total:** |
| --- | --- | --- | --- |
| CIT Relay and Switch, ANT11SF1CQE (Switch) | 1 | $3.48 | $3.48 |
| SunLED, XLUG12D (Green LED) | 10 | $3.00 |  |
| Kingbright, WP7113ID (Red LED) | 10 | $3.40 |  |
| Ohmite, WHD250FET (250 Ohm Resistor) | 21 | $11.34 |  |
| Arduino Uno REV3 [A000066] (Arduino) | 1 | $27.60 |  |
| KINGSTATE KPEG242 (Buzzer) | 1 | $2.13 | |


| **Item:** | **URL** |
| --- | --- |
| CIT Relay and Switch, ANT11SF1CQE (Switch) |  https://www.digikey.com/en/products/detail/cit-relay-and-switch/ANT11SF1CQE/12503396 |
| SunLED, XLUG12D (Green LED) | https://www.digikey.com/en/products/detail/sunled/XLUG12D/4745838 |
| Kingbright, WP7113ID (Red LED) | https://www.digikey.com/en/products/detail/kingbright/WP7113ID/1747663 |
| Ohmite, WHD250FET (250 Ohm Resistor) | https://www.digikey.com/en/products/detail/ohmite/WHD250FET/16839029 |
| Arduino Uno REV3 [A000066] (Arduino) | https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/ref=asc_df_B008GRTSV6?tag=bngsmtphsnus-20&linkCode=df0&hvadid=79852149837934&hvnetw=s&hvqmt=ehvbmt=be&hvdev=c&hvlocint=&hvlocphy=&hvtargid=pla-4583451676566041&th=1 |
| KINGSTATE KPEG242 (Buzzer) | https://www.newark.com/kingstate/kpeg242/piezo-buzzer-4-1khz-70db/dp/61M7049?mckv=s_dc|pcrid||plid||kword||match|e|slid||product|61M7049|pgrid|1231453304461926|ptaid|pla-4580565455222458|&msclkid=4ff6ddb1429613a4db67bb914883a843&CMP=KNC-BUSA-GEN-Shopping-ALL |


## References
1. A. Hadhazy, “What are the limits of human vision?,” BBC News, https://www.bbc.com/future/article/20150727-what-are-the-limits-of-human-vision (accessed Apr. 17, 2024). 
2. “What is the human hearing range in hz and DB?: Miracle-ear,” Miracle Ear, https://www.miracle-ear.com/blog-news/human-hearing-range (accessed Apr. 17, 2024). 
3. “Ant11sf1cqe CIT relay and switch | switches | DigiKey,” Digikey, https://www.digikey.com/en/products/detail/cit-relay-and-switch/ANT11SF1CQE/12503396 (accessed Apr. 16, 2024). 
4. https://www.digikey.com/en/products/detail/vishay-semiconductor-opto-division/VLCS5130/4073547  (RED LED)
5. https://www.digikey.com/en/products/detail/american-bright-optoelectronics-corporation/BL-BGX3V1/9678159 (GREEN LED)
6. https://theengineeringmindset.com/led-resistor-calculator/ (FORMULA)
7. https://www.vishay.com/docs/81938/vlcs5130.pdf (RED DATA SHEET)
8. https://www.americanbrightled.com/pdffiles/led-components/through-hole/BL-BGX3V1.pdf (GREEN DATA SHEET)
9. https://www.digikey.com/en/products/detail/lumimax-optoelectronic-technology/MF1-8W75RFTB/16708261 (75 OHM RESISTOR)
10. https://www.digikey.com/en/products/detail/vishay-dale/CMF5550R000FKEK70/3616606 (50 OHM RESISTOR)
11. “A000066-datasheet.pdf,” Ardui Uno R3, https://docs.arduino.cc/resources/datasheets/A000066-datasheet.pdf (accessed Apr. 16, 2024). 
12. “KPEG242 - Transducer, Piezo, buzzer, audio indicator, continuous, 3 V, 16 V, 7 ma, 70 DB,” Newark, https://www.newark.com/kingstate/kpeg242/piezo-buzzer-4-1khz-70db/dp/61M7049?mckv=s_dc%7Cpcrid%7C%7Cplid%7C%7Ckword%7C%7Cmatch%7Ce%7Cslid%7C%7Cproduct%7C61M7049%7Cpgrid%7C1231453304461926%7Cptaid%7Cpla-4580565455222458%7C&msclkid=4ff6ddb1429613a4db67bb914883a843&CMP=KNC-BUSA-GEN-Shopping-ALL (accessed Apr. 17, 2024).

‌
