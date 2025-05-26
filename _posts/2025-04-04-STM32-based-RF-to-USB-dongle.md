---
layout: post
title: "STM32 based RF-to-USB dongle"
categories: project
tags: [STM32, NRF24, PCB]
---

STM32L4-based RF-to-USB dongle using the wireless **NRF24** 2.4 GHz transceiver. The board includes a USB-A connector on one side and a female SMA antenna connector on the other. It is a 4-layer PCB created using KiCad measuring **50 mm x 20 mm**.

| ![RF2USB](/assets/img/pcb/pcb-rf2usb.png){:.ioda} |

The boards were ordered from JLCPCB, and the assembly was done **manually** using a hot plate and a rework station. I used STM32CubeIDE and the HAL provided by the manufacturer for writing the firmware. For the OLED display, I found a [library](https://github.com/afiskon/stm32-ssd1306) which works with OLEDs based on SSD1306 driver. The nRF24 driver required more work, and is being constructed step by step. A state machine is running in the main loop, different functionalities can be chosen by using the push buttons on the board.

| ![RF2USB](/assets/img/projects/rf2usb/rf2usb2.png) | ![RF2USB](/assets/img/projects/rf2usb/rf2usb1.png) |

The project status is tracked on [github.com/RemiFM/RF-to-USB](https://github.com/RemiFM/RF-to-USB/tree/main). The next step will be manual assembly using solder paste and hot air. Hereafter, the firmware will be finalised and tested. Updates soon!

| ![RF2USB](/assets/img/pcb/schematic-rf2usb.png){:.ioda} |