# Introduction

At the beginning of November, I wanted to create a camera gimbal as a side project. It seemed simple enough; I just needed some servo motors and a gyroscope, and I figured the rest would fall into place. I came across plenty of camera gimbal Arduino projects online, but I wanted the project to be bootstrap. Additionally, the Arduino projects I saw had some major shortcomings that were unacceptable to me. Surprisingly, the biggest shortcoming is functionality as an actual gimbal! The hobby servos used in these sorts of projects do not provide a smooth enough rotation for practical purposes.

Upon further research, I found that *actual* gimbals use brushless DC motors, (BLDCs), because of their smoother control, quiet operation, and power efficiency. This discovery led me down a massive rabbit hole as I asked myself: "How am I going to control the motor?" Turns out that there are plenty of BLDC motor drivers on the market, including the [Tinymovr,](https://tinymovr.com/en-us) or the [Odrive,](https://odriverobotics.com/?srsltid=AfmBOornOrGTfZCiD05f8jtOMgs2SLPtsRMCaBWyb3TLv5Ix27u7qMqg) but where is the learning in that? As a mechatronics engineering student, I knew I wanted to move away from mechanical work so this project was the perfect opportunity to develop my electrical and embedded skills at a low level. After some additional thinking, I focused my scope in on developing my own field-oriented controller to precisely control a brushless DC motor. 

## Who is This Reading For?

This `README.md` document will serve to document my journey and design process as someone, who quite frankly, has no idea what they are doing. Perhaps this is misuse of what Github is intended for, but I just needed somewhere on the cloud to document my workflow. The rest of this document will read as a blog or instructable and can be read top down. I intend that anyone who reads this document, (once completed,) will be able to create their own BLDC motor driver while gaining insight into my learning process along the way. I intend that the only prerequisite knowledge required to understand this document is a basic circuits course, and thus will keep the language as simple as possible. I have created a [glossary](#Glossary) of technical terms to aid the reader in comprehension.

# High-Level Understanding

## How do Brushless DC Motors Work?

## What is Field Oriented Control?

Field-oriented control (FOC), also known as vector control, is a method of controlling 3-phase motors such as BLDCs by decoupling and independently controlling the torque and flux. As the term vector control suggests, this is done by transforming the three-phase currents into two orthogonal vectors. This is accomplished by the Clarke and Park transformations, producing the vectors I<sub>d</sub>, which control the flux, and I<sub>q</sub>, which controls the torque.

If this project aims to achieve precise position control, it may not be immediately evident why FOC is necessary. You could use a motor encoder and then send currents into the three phases accordingly using other commutation methods. Indeed, FOC *is not* strictly required for position control of a motor but offers many benefits, especially for applications in gimbals. FOC provides better power efficiency, torque characteristics, and smoother commutation.

## Block Diagram

![Block diagram of motor controller](Images/block-diagram.svg)
*Field-oriented controller block diagram. Original creation.*

# First Design

For the first iteration of the design, I thought it would be wise to use breakout boards to prove to myself that I can get this to work else I design an overpriced, non-functional PCB.

## Component Selection

* Since I wanted to use breakout boards, I needed widely available ICs. 
* Since the first design is a proof-of-concept, I chose a small hobby gimbal motor so I did not have to worry about making sure my components were rated for high power. 
* Some 3-phase inverter ICs are specifically made for BLDC operation, and include current sensors in their package. However, for the sake of learning, I decided on separate current sensors and inverters. 
* For the MCU, I initially wanted to choose an Arduino Nano for its form factor. However, it only has 6 PWM channels, which is only enough to control the motor as the board requires 6 inputs. If I wanted PWM anywhere else in the design, it would not be sufficient. Because of this, I decided to use the ESP32 DEVKIT V1 board because it has 16 pins that support PWM. For the second iteration, I may use the Teensy board which has a whopping 31 PWM channels, but with the tradeoff of being 3x more expensive.

| Description | PN |
| --- | --- |
| Magnetic Encoder | [AS5600](https://www.amazon.com/Magnetic-Encoder-Induction-Measurement-Precision/dp/B094F8H591?th=1) |
| MCU | ESP32 DEVKIT V1 |
| BLDC | TBD |
| Power Supply | TBD |
| Current Sensor | [INA3221](https://www.amazon.com/DAOKAI-INA3221-Channel-Current-Replacement/dp/B0B5D3PVFR/ref=sr_1_2?crid=KPTQXU6AVIML&dib=eyJ2IjoiMSJ9.ROfuRmnt7fyonseZ5LHUXL2l47dBgxdrTOMYApPNdhPdyjwZEU6cm2AWRfzulQoaKRz_KolXH0dgz6UZqttZ7wL75fTOVbobFJQuQjU_TnWBuNShv56PupeN65hO1czEBZp7WDB4j-woHkOQKQtNwc8NBXwqaWbqXfgtErMfGvOoqAifkzuwKvcBpvwJ7_cXCyxPZUcKcO0OYuHajSs0lCFSzxuGfggV1VItRCouimY.7OSrFlWi814gCHG7CSV7sCe8t8Lu424Qw6H9MTYB_6o&dib_tag=se&keywords=INA3221&qid=1731987102&sprefix=ina3221%2Caps%2C105&sr=8-2#customerReviews) |
| 3-Phase Inverter | [TMC6300](https://www.amazon.com/SparkFun-Brushless-Motor-Driver-Dimensions/dp/B0C9PJWGW4) |

## Magnet Bracket

Because I am using a magnetic encoder, I need a way to mount a magnet to the motor shaft. I designed and 3D printed a bracket using Solidworks. The magnet fits in via a press fit.

## Schematic

## Software

### I2C

## PI Controls

# Second Design

# Further Reading

The following resources were extremely helpful in the process of designing my field-oriented controller.

[Brushless Motor Control with Simulink](https://www.youtube.com/playlist?list=PLn8PRpmsu08qL-EG3DRMtRyokpXQJyhp7)

# Glossary

| Term | Description |
| --- | --- |
| Commutation | TBD |
| Field Oriented Control (FOC) | TBD |
| Brushless DC Motor (BLDC) | TBD |
| Park Transform | TBD |
| Clarke Transform | TBD |

