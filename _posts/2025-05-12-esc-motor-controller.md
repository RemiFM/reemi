---
layout: post
title: "ESC for Motor Control Evaluation"
categories: project
tags: [STM32, ESC, PCB]
---

This page will be used to track my progress in the creation of a STM32-based ESC motor controller. The board will be designed to test various motor control algorithms like 6-step control and **sensorless FOC** (field-oriented control). I defined the following requirements:

- **3-5S** LiPo input (11.1-21V)
- **45A** continuous current
- Current & voltage sensing on all phases
- CAN, UART, SWD & I2C interfaces
- 6-layer board, 2oz on outer layers, 0.5oz on inner layers
- Small form factor[^1], suitable for UAV applications

Some interesting resources I will consult during the design are the open source VESC project and the STMicroelectronics B-G431B-ESC1 discovery kit. Both have detailed schematics and documentation available. 

The schematic is based around the **STM32G4** microcontroller, mixed-signal MCU's with DSP and FPU instructions aimed at motor control and digital power applications. Three single half-bridge drivers are used instead of a single three-phase driver to benefit the layout of the board. The STL225N6F7AG **60V, 120A MOSFET** with an on-resistance of 1.2mOhm is used. 


| ![pcb](/assets/img/projects/esc-motor/power_schematic.png){:.ioda} |

[^1]: I ran into a dilemma. Initially I wanted to have small SMT components on both sides of the final PCB assembly. But since I will be the one assembling the board, this might not be the best idea. I have decided the majority of components will come on a single side of the board making the result a bit larger than initially expected. This choice will help me keep my sanity during assembly and troubleshooting.

