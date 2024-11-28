# DIY-a-200W-Precise-Electronic-Load
An electronic load that comes with a minimal onboard circuitry, a simple DIY 200W load.
See all details of the project from here: 

Whenever I want to test some USB power supplies, drawing I-V characters of a power supply and working on a lab bench supplies based on SMPS and linear mode I face the problem of testing its full capabilities. Usually I want to see how much power I can get as an output from a unit to test the best method to connect a low value resistance between its output wires through a multimeter in ammeter mode. The value of resistance and voltage across the power supply is responsible for the current which is basically Ohm’s law. But how to decide the value of that resistance, if its value is higher than recommended one it will not draw max current and if it’s value is lower it shorts the output and turns on the protection feature. And if we are measuring higher current say 10A then a higher wattage low value resistance is required. All this is not possible at a time and took a lot of precision to accurately characterize a power supply unit.

That’s why electronic loads came into the picture, in which the resistance can be variable or we can say they can draw a constant current out of any device. I made this electronic load from scratch, which has a max capability to draw 200W. This is a huge power, the concept of electronic load is based on heat dissipation, they convert this power into heat with the help of big mosfets. The basic working of a constant current load is stated in the section below. I made a PCB combning all the features, Big thanks to PCBWay for sponsoring the PCBs for this project! Their high-quality manufacturing and quick turnaround made this build possible.

How an Electronic Load works:

Suppose you have a 3V battery and would like to discharge it with a constant current of 1 A. The operating point is the (voltage and current) setpoint where the battery output voltage intersects the programmed constant current load line of the electronic load. When the load operates in CC mode, it loads the output of an external voltage source (for example, a 3 V battery), with a variable resistor to reach the desired programmed current. Most electronic loads use power transistors, FET’-s or IGBT’-s that act as a variable resistor to regulate the current flowing into the load.

The transistors are typically arranged in a parallel array configuration to handle more power. The current flowing into the load is monitored via a shunt resistor (for example 1 Ω). The voltage drop proportional to I*Rshunt is fed to a current amplifier. The current amplifier compares the voltage drop on the current shunt against the reference programmed value (example 1 A * 1 Ω = 1 V). The amplifier output signal regulates the FET resistance and electronic load’s input current. This feedback configuration allows the load to dynamically change the resistance and maintain the programmed current independent of the voltage change of your sourcing device.

The ability to sink high currents at exceptionally low voltages is challenging and a highly required feature for electronic loads. Sinking at low voltages is mandatory when testing fuel cells, power management ICs, or other devices operating at low voltages and high currents.

Circuit Diagram:

I have taken the reference from a lot of sources and finally came up with this approach of keeping two MOSFETs in parallel to each other. The schematic is divided into 5 main sections.
First section is the input section, which is a basic input section and this load needs a 12V external power supply which is different from the test supply to work. Because of onboard electronics and operational amplifiers.

Second section is a basic voltage set section, it is basically a voltage divider network which feeds the non inverting supply of the operational amplifier. This section has two potentiometers, one to adjust coarse and other for fine adjustment. The voltage output from this section is made equivalent to the current drawn from the test supply. Which is based on the 3rd section operational amplifier mathematics. So a simple voltmeter is used to get the current value.

Third section is the main electronic load section, the operational amplifiers one as comparator and other as non inverting amplifiers are used to get the feedback from section 4 and set the operating point of the MOSFET.

Section 4 is a basic MOSFET load section in which 0.33Ohm resistors are used as a shunt to measure the voltage drop across that resistor and convert it into respective operating point voltage values to control the current.

Section 5 is the output section, containing pin headers to plug and test any load.

Components Required:

IRFP260N N channel Mosfet

LM324 Operational amplifier

100K, 10K potentiometers

Decoupling capacitor 100n, 10uf

10K, 4.7k and 1K resistor

10K SMD potentiometers

0.33Ohm 5W resistor

3 wire voltmeter

12v adapter

PCB from PCBWAY

PCB Design:

The PCB is designed in such a manner that both the MOSFETS are placed in the bottom plane to mount the whole system on a heatsink platform. All the other circuitry is placed on the top side of the PCB. The operational amplifier section has two onboard potentiometers to adjust the operating point of the MOSFET. We have to adjust them once while powering up to calibrate the output current according to the current shown by the voltmeter. Both the coarse and fine adjustments are kept at the front section to access freely. The points on the PCB are given to mount a 3 wire voltmeter there.
Special thanks to PCBWay for sponsoring the PCBs. Their quality and service are unmatched in the industry! Sign-up now and get free coupons on your next order. All the required files Gerber, BOM and CPL are uplaoded on PCBWAY hub, can be downlaoded from there. 

Adding a Heatsink:

Because we are only using a passive cooling system here, the best idea is to get a huge heatsink plate. The heatsink can be selected such that it can dissipate power up to 200W. Keep the two MOSFET isolated from each other while mounting on the heatsink and use the plastic screws if available any wrong connection may damage the whole unit.

Working Procedure:

Connect the power supply 12v 1A. Then use a lab bench power supply as a test load and use onboard voltmeter to calibrate the SMD potentiometers. After calibration we are ready to go and test any of the battery, Power supply and USB output.

Testing the Load:

I tested this electronic load under different conditions, the accuracy is +-5%, which I think is good for a 0-10A range. The fine adjustment works as well. Moreover the load can draw a max of 300W according to the transistor datasheet. But recommend to use within 200W. Moreover the voltmeter shows accurate readings here are some tests:

Test with power supply at low current:

Test with power supply at high current:

Test with USB PD at variable current:

All the required files Gerber, BOM and CPL are uplaoded on PCBWAY hub, can be downlaoded from there. Once again thanks to PCBWAY for sponsoring this PCB project. 
