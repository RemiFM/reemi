---
layout: post
title: "ESC for Motor Control Evaluation"
categories: project
tags: [STM32, ESC, PCB]
---

This page will be used to track my progress in the creation of a STM32-based ESC motor controller. The board will be designed to test various motor control algorithms like 6-step control and **sensorless FOC** (field-oriented control). I defined the following requirements:

- 3-5S LiPo input (11.1-21V)
- 45A continuous current
- Current & voltage sensing on all phases
- CAN, UART, SWD & I2C interfaces
- 6-layer board, 2oz on outer layers, 0.5oz on inner layers
- Small form factor, suitable for UAV applications

Some interesting resources I will consult during the design are the open source VESC project and the STMicroelectronics B-G431B-ESC1 discovery kit. Both have detailed schematics and documentation available. 

The schematic is based around the STM32G4 microcontroller, mixed-signal MCU's with DSP and FPU instructions aimed at motor control and digital power applications. Three single half-bridge drivers are used instead of a single three-phase driver to benefit the layout of the board. The STL225N6F7AG 60V, 120A MOSFET with an on-resistance of 1.2mOhm is used. 


| ![pcb](/assets/img/projects/esc-motor/power_schematic.png){:.ioda} |

Currently, I am in progress with the layout of the board. Only the power stage is shown in the schematic above.