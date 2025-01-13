---
layout: post
category: test
---

My master thesis covered the topic of the design and validation of a resonant switching LLC DC/DC converter for the auxilariy systems of a solar car. These low-power (<25W) auxilary systems include the vehicle dashboard, communication modules, brake lights, horn, blinkers... The converter has to work for a wide range (difference of 80V) of input voltages due to the battery system connected to the input.

| ![pcb](/assets/img/pcb/pcb-llc-half-bridge.jpg){:.ioda} |

Both half-bridge and full-bridge rectification variants were created. The ICE2HS01G IC by Infineon was used. The final esults were underwhelming, the LLC converter was not deemed suitable for a low power application due to its complexity and large BOM.

| ![pcb](/assets/img/pcb/pcb-llc-full-bridge.jpg){:.ioda} |