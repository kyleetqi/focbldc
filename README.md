# Field Oriented Control of a Brushless DC Motor

## Introduction

At the beginning of November, I wanted to create a camera gimbal as a side project. It seemed simple enough; I just needed a servo motor and a gyroscope to command it, and the rest would fall into place. There are plenty of camera gimbal Arduino projects online that are easy to follow, but I wanted this project to be boostrap. Additionally, the Arduino projects I saw had some major shortcoming that were unacceptable to me. Surprisngly, the biggest shortcoming is functionality as an actual gimbal! The hobby servos used in these sorts of projects do not provide a smooth enough rotation.

Upon further research, I found that actual gimbals use brushless DC motors, (BLDCs), because of its smoother control, quiet operation, and power efficiency, which are all desirable characteristics in a gimbal. But this discovery led me down a massive rabbit hole as I asked myself: "How am I going to control the motor?" Turns out that there are plenty of BLDC motor drivers on the market, including the [Tinymovr,](https://tinymovr.com/en-us) or the [Odrive,](https://odriverobotics.com/?srsltid=AfmBOornOrGTfZCiD05f8jtOMgs2SLPtsRMCaBWyb3TLv5Ix27u7qMqg) but where is the learning in that? As a mechatronics engineering student, I knew I wanted to move away from mechanical work so this project was the perfect opportunity to develop my electrical and embedded skills at the lowest level possible. After some additional digging, I focused my scope in on developing my own field oriented controller to precisely control a brushless DC motor.

### Who is This Reading For?

This `README.md` document will serve to document my journey and design process as someone, who quite frankly, has no idea what they are doing. Perhaps this is missuse of what Github is intended for, but I just needed somewhere on the the cloud to document my workflow. The rest of this document will read as a blog or instructable, and can be read top down. I intend that anyone who reads this document, (once completed,) will be able to create their own BLDC motor driver, while gaining insight into my learning process along the way.

## High-Level Understanding

### What is Field Oriented Control?

Field oriented control (FOC), also known as vector control, is a method of controlling 3-phase motors such as BLDCs by decoupling and independently controlling the torque and flux. As the term vector control suggests, this is done by transforming the three phase currents into two orthagonal vectors. This is accomplished the Clarke and Park transformations, producing the vectors I<sub>d</sub>, which control the flux, and I<sub>q</sub>, which controls the torque.

If the goal of this project is to achieve precise position control, it may not be immediately evident why FOC is necessary. 

### Block Diagram

![Block diagram of motor controller](Images/block-diagram.svg)

## Component Selection

| Description | PN |
| --- | --- |
| Magnetic Encoder | AS5600 |
| MCU | Arduino Nano |
| BLDC | TBD |
| Power Supply | TBD |
| Current Sensors | TBD |

### Additional Components

* Resistors as required
* Capacitors as required

## PI Controls

## Software

### I2C

## First Design

## Mechanical Considerations

## Second Design: Custom PCB
