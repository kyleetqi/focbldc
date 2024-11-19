# Field Oriented Control of a Brushless DC Motor

## Introduction

At the beginning of November, I wanted to create a camera gimbal as a side project. It seemed simple enough; I just needed some servo motors and a gyroscope, and I figured the rest would fall into place. I came across plenty of camera gimbal Arduino projects online, but I wanted the project to be bootstrap. Additionally, the Arduino projects I saw had some major shortcomings that were unacceptable to me. Surprisingly, the biggest shortcoming is functionality as an actual gimbal! The hobby servos used in these sorts of projects do not provide a smooth enough rotation for practical purposes.

Upon further research, I found that *actual* gimbals use brushless DC motors, (BLDCs), because of their smoother control, quiet operation, and power efficiency. This discovery led me down a massive rabbit hole as I asked myself: "How am I going to control the motor?" Turns out that there are plenty of BLDC motor drivers on the market, including the [Tinymovr,](https://tinymovr.com/en-us) or the [Odrive,](https://odriverobotics.com/?srsltid=AfmBOornOrGTfZCiD05f8jtOMgs2SLPtsRMCaBWyb3TLv5Ix27u7qMqg) but where is the learning in that? As a mechatronics engineering student, I knew I wanted to move away from mechanical work so this project was the perfect opportunity to develop my electrical and embedded skills at a low level. After some additional thinking, I focused my scope in on developing my own field oriented controller to precisely control a brushless DC motor. 

### Who is This Reading For?

This `README.md` document will serve to document my journey and design process as someone, who quite frankly, has no idea what they are doing. Perhaps this is misuse of what Github is intended for, but I just needed somewhere on the cloud to document my workflow. The rest of this document will read as a blog or instructable and can be read top down. I intend that anyone who reads this document, (once completed,) will be able to create their own BLDC motor driver while gaining insight into my learning process along the way. I intend that the only prerequisite knowledge required to understand this document is a basic circuits course, and thus will keep the language as simple as possible. I have created a [glossary](#Glossary) of technical terms to aid the reader in comprehension.

## High-Level Understanding

### How do Brushless DC Motors Work?

### What is Field Oriented Control?

Field oriented control (FOC), also known as vector control, is a method of controlling 3-phase motors such as BLDCs by decoupling and independently controlling the torque and flux. As the term vector control suggests, this is done by transforming the three-phase currents into two orthogonal vectors. This is accomplished by the Clarke and Park transformations, producing the vectors I<sub>d</sub>, which control the flux, and I<sub>q</sub>, which controls the torque.

If this project aims to achieve precise position control, it may not be immediately evident why FOC is necessary. You could use a motor encoder then send currents into the three phases accordingly using other commutation methods. Indeed, FOC *is not* strictly required for position control of a motor but offers many benefits, especially for applications in gimbals.

The simplest method of commutation is trapezoidal.

In contrast, FOC eliminates these issues:

* __Power Efficiency:__ 
* __Smooth Operation:__ FOC 
* __Torque Control:__ FOC provides precise torque control, critical for dynamic loads such as those experienced in a camera gimbal.

### Block Diagram

![Block diagram of motor controller](Images/block-diagram.svg)

## Component Selection

After doing some research, 

| Description | PN |
| --- | --- |
| Magnetic Encoder | AS5600 |
| MCU | Arduino Nano |
| BLDC | TBD |
| Power Supply | TBD |
| Current Sensor | INA3221 |
| 3-Phase Inverter | TBD |

* Resistors as required
* Capacitors as required

Some 3-phase inverter ICs are specifically made for BLDC operation, and include current sensors in their package. However, for the sake of learning, I will use separate current sensors and inverters for the first iteration of the design.

## First Design

The first design will use breakout boards.

### Schematic

## Software



### PI Controls

### I2C

## Second Design: Custom PCB

## Glossary

| Term | Description |
| --- | --- |
| Commutation | TBD |
| Trapezoidal Commutation | TBD |
| Field Oriented Control (FOC) | TBD |
| Brushless DC Motor (BLDC) | TBD |
| Park Transform | TBD |
| Clarke Transform | TBD |

