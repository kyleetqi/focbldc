# Field Oriented Control (FOC) of a Brushless DC Motor

## Introduction

At the beginning of November, I wanted to create a camera gimbal as a side project. It seemed simple enough; I just needed a servo motor and a gyroscope to command it, and the rest would fall into place. There are plenty of camera gimbal Arduino projects online that are easy to follow, but I wanted this project to be boostrap. Additionally, the Arduino projects I saw had some major shortcoming that were unacceptable to me. Surprisngly, the biggest shortcoming is functionality as an actual gimbal! The hobby servos used in these sorts of projects do not provide a smooth enough rotation.

Upon further research, I found that actual gimbals use brushless DC motors, (BLDCs), because of its smoother control, quiet operation, and power efficiency, which are all desirable characteristics in a gimbal. But this discovery led me down a massive rabbit hole as I asked myself: "How am I going to control the motor?" There are plenty of BLDC motor drivers on the market, including the [Tinymovr,](https://tinymovr.com/en-us) or the [Odrive,](https://odriverobotics.com/?srsltid=AfmBOornOrGTfZCiD05f8jtOMgs2SLPtsRMCaBWyb3TLv5Ix27u7qMqg) but where is the learning in that? As a mechatronics engineering student, I knew I wanted to move away from purely mechanical work so this project was the perfect opportunity to develop my electrical and embedded skills at the lowest level possible.

### Who is This Reading For?

This `README.md` document will serve to document my journey and design process as someone, who quite frankly, has no idea what they are doing. Perhaps this is missuse of what Github is intended for, but I just needed somewhere central to document my workflow. The rest of this document will read as a blog or instructable, designed to be read top down. I intend that anyone who reads this will be able to create their own BLDC motor driver by the end of it, while documenting my learning process along the way.

## High-Level Understanding

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
