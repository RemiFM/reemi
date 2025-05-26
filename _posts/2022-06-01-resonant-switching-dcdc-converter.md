---
layout: post
category: test
---

My master thesis covered the topic of the design and validation of a **resonant switching LLC DC/DC** converter for the auxilariy systems of a solar car. These **low-power (<25W)** auxilary systems include the vehicle dashboard, communication modules, brake lights, horn, blinkers... The converter has to work for a **wide range (~90V - 170V)** of input voltages due to the battery system connected to the input.

| ![pcb](/assets/img/pcb/pcb-llc-half-bridge.png){:.ioda} |

Designing the resonant tank (LLC) of the converter is a crucial but difficult process. Using the first harmonic approximation method, a transfer function can be constructed which prescribes the behaviour of the converter at different switching frequencies. Another difficulty was the realisation of our own magnetic components. Multiple transformer configurations were constructed and compared.

| ![llc](/assets/img/projects/thesis_llc/transferfunctie_finaal.png) | ![llc](/assets/img/projects/thesis_llc/wikkelmethoden_foto.jpg) |

Both half-bridge and full-bridge rectification variants were created using **Altium Designer**. The ICE2HS01G IC by Infineon was used. The final esults were underwhelming, the LLC converter was not deemed suitable for a low power application due to its complexity and large BOM.


| ![llc](/assets/img/projects/thesis_llc/pcb_bovenzijde-1.png) | ![llc](/assets/img/projects/thesis_llc/pcb_onderzijde-1.png) |