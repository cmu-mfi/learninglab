# IoT and Sensor Integration

Internet of Things + MQTT sensor,input, actuator, motor drive learning board. Can be powered with a power drill battery for immediate remote deployment and sensor monitoring.
Learning Goal: Quick start "how to" develop and build your own IIoT solution with scale and affordability in mind using off-the-shelf hardware and lightweight software.

#Hardware Rev 1.0*: 
    Microcontroller: ESP32-WROOM-32
    Sensors: 
        Temperature and Humidity (SHT45), 
        Voltage, Current, Power (INA260),
        Pushbutton(x4),
        Rotary Enocder
    Actuators:
        Relay (10A, 277VAC, 30VDC),
        DRV8871 (DC Motor Drive),
        A4988 (Stepper Motor Drive)
    Output: 
        RGB LED(x4),
        OLED (128x64 pixel)
        Buzzer

Schematic 
KiCAD Design files:


## Bill of Materials

| Reference                                                                 | Value                   | Qty | DigiKey P/N                     | Adafruit P/N | AliExpress / Amazon Link                                                                 |
|---------------------------------------------------------------------------|-------------------------|----:|---------------------------------|--------------|------------------------------------------------------------------------------------------|
| BZ1                                                                       | Buzzer_5V               |   1 | 445-2525-1-ND                   |              |                                                                                          |
| C3, C4, C7                                                                | 0.1uF 50V               |   3 | 1276-1068-1-ND                  |              |                                                                                          |
| C10, C11                                                                  | 0.22uF 50V CER          |   2 | 445-2283-1-ND                   |              |                                                                                          |
| C12, C13, C14                                                             | 22uF 50V                |   3 | 399-11438-1-ND                  |              |                                                                                          |
| D2                                                                        | D                       |   1 | S5AC-FDICT-ND                   |              |                                                                                          |
| D10                                                                       | LED                     |   1 | EALP05RDHRA2-ND                 |              |                                                                                          |
| D12                                                                       | SMF15A                  |   1 | SMF15A-E3-08CT-ND               |              |                                                                                          |
| D14                                                                       | 1N4148W                 |   1 | 4878-1N4148WCT-ND               |              |                                                                                          |
| J3                                                                        | ServoPort_04            |   1 | S1012EC-40-ND                   |              |                                                                                          |
| J5, J8                                                                    | Screw_Terminal_2_P3.50mm|   2 | 732-2747-ND                     |              |                                                                                          |
| J7                                                                        | PINHD_2x3_Male          |   1 | S1012EC-40-ND                   |              |                                                                                          |
| J15                                                                       | Screw_Terminal_3_P5.00mm|   1 | 277-1578-ND                     |              |                                                                                          |
| K1                                                                        | G5Q-1                   |   1 | Z2929-ND                        |              |                                                                                          |
| Q1                                                                        | MOSFET P-CH 30V 25A TO252|  1 | 785-1106-1-ND                   |              |                                                                                          |
| Q2, Q3                                                                    | MMBT2222A               |   2 | MMBT2222ATPMSCT-ND              |              |                                                                                          |
| R1, R2, R8, R22, R25, R26, R27, R28, R30, R34, R35, R36, R37, R38         | 10K                     |  14 | 311-10.0KFRCT-ND                |              |                                                                                          |
| R3, R4, R5, R6, R7, R9, R16, R23                                          | 220                     |   8 | 311-220FRCT-ND                  |              |                                                                                          |
| R17, R21, R31                                                             | 330                     |   3 | 311-330FRCT-ND                  |              |                                                                                          |
| R18, R19, R20, R32                                                        | 1K                      |   4 | 311-1.00KFRCT-ND                |              |                                                                                          |
| R33                                                                       | 100k                    |   1 | 311-100KFRCT-ND                 |              |                                                                                          |
| S1                                                                        | SPDT Switch             |   1 | EG5617-ND                       |              |                                                                                          |
| SW1, SW2, SW3, SW4                                                        | Push_Button             |   4 | 2223-TS02-66-60-BK-160-LCR-D-ND |              |                                                                                          |
| SW6                                                                       | RotaryEncoder_Switch_MP |   1 | PEC11R-4220F-S0024-ND           |              |                                                                                          |
| U3                                                                        | PCA9685PW               |   1 | 568-11925-1-ND                  |              |                                                                                          |
| U4                                                                        | SHT45                   |   1 |                                 | 6174         |                                                                                          |
| U7                                                                        | A4988                   |   1 |                                 | 6109         |                                                                                          |
| U8                                                                        | INA260                  |   1 |                                 | 4226         |                                                                                          |
| U14                                                                       | MAX40200AUK             |   1 | 175-MAX40203AUK+TCT-ND          |              |                                                                                          |
| U15                                                                       | L7805                   |   1 | 497-7255-1-ND                   |              |                                                                                          |
| U18, U19                                                                  | MP1584                  |   2 |                                 |              | [AliExpress Link](https://www.aliexpress.us/item/3256806890547813.html)                  |
| U21                                                                       | ESP32                   |   1 |                                 |              | [Amazon Link](https://www.amazon.com/gp/product/B0D8Q8XFRK/) _(beware pinout)_            |

*Hardware fix list:
    1) The INA260 power sensor is upstream the reverse Polarity circuit. Will blow the INA260 but everything is fine.
    2) The Stepper Sleep pin is not wired, so steppers with active code always consume power, no way to put them to sleep without bodge wire. 
    3) Change ESP32 and footprint to digikey p/n (1965-ESP32-DEVKITC-32UE-ND) for posterity