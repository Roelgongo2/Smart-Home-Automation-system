Smart Home Automation Project
This project controls a smart home system using an Arduino Uno R3. It integrates multiple sensors and actuators to provide automated lighting, temperature control, door operation, and gas leak safety.

Features
Lighting Control: The light bulbs automatically adjust their brightness inversely to the room’s ambient light (using a Photoresistor).
Temperature Control: The DC fans automatically adjust their speed based on the room temperature (using a TMP36 sensor).
Door Operation: The doors automatically open when someone approaches (using an Ultrasonic sensor and Servos).
Power Saving Mode: When no motion is detected for 10 seconds (via PIR sensor), the system goes into standby, turning off fans, lights, and closing doors.
Gas Safety Alarm: If the Gas Sensor detects high gas concentration, the system overrides all normal operations. It opens the doors, turns fans to maximum speed for ventilation, turns on the lights, and displays a warning on the LCD.
Hardware Components
1x Arduino Uno R3
1x Gas Sensor (MQ Series)
1x Temperature Sensor (TMP36)
1x Ultrasonic Distance Sensor (4-pin HC-SR04)
1x LCD 16x2 (Parallel)
1x PIR Sensor
1x Photoresistor (LDR)
2x Positional Micro Servo (Doors)
2x DC Motor (Fans)
2x Light Bulb
4x nMOS Transistor (MOSFET) (For driving Motors and Bulbs)
Resistors (1kΩ, 156Ω)
Power Supplies (12V for Motors/Bulbs, 5V for Logic/Sensors)
Wiring Guide
Sensors (Inputs)
Component	Arduino Pin	Notes
MQ Gas Sensor	A0	Analog output to A0. Requires 5V and GND.
TMP36 Temp Sensor	A1	Vout to A1. Power with 5V and GND.
LDR (Photoresistor)	A2	Connect with a 1kΩ pull-down resistor to GND to form a voltage divider.
PIR Sensor	D2	Digital output to D2.
Ultrasonic Echo	D4	Echo pin.
Ultrasonic Trig	D7	Trig pin.
Actuators (Outputs)
(Note: DC Motors and Light Bulbs require higher current and voltage than the Arduino can provide. They must be driven using the nMOS Transistors (MOSFETs) connected to the external power supply.)

Component	Arduino Pin	Notes
DC Motor 1 (Fan 1)	D3 (PWM)	Connect D3 to MOSFET Gate. Source to GND, Drain to Motor negative.
DC Motor 2 (Fan 2)	D5 (PWM)	Connect D5 to MOSFET Gate.
Light Bulb 1	D6 (PWM)	Connect D6 to MOSFET Gate.
Light Bulb 2	D11 (PWM)	Connect D11 to MOSFET Gate.
Servo 1 (Door 1)	D9	PWM control signal.
Servo 2 (Door 2)	D10	PWM control signal.
LCD 16x2 Display (Parallel Mode)
LCD Pin	Arduino Pin
RS	D8
EN	D12
D4	D13
D5	A3
D6	A4
D7	A5
(Also connect VSS, RW, K to GND. VDD, A to 5V. V0 to a potentiometer for contrast).	
Usage
Assemble the circuit according to the wiring guide.
Ensure the external 12V/5V power supplies share a common ground with the Arduino.
Flash the code to the Arduino Uno using Embedr IDE.
The system will start in normal mode and adjust automatically based on the sensor inputs!
