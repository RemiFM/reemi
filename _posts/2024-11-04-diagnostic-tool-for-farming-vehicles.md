---
layout: post
category: example
---

Agricultural vehicles often face wire harness issues due to the harsh environments in which they operate. Factors such as water ingress, punctures, ruptures, or structural damage to cables can significantly impact their performance. During the design phase, vehicle engineers struggle to **identify potential failure points or weak spots in the wire harness**. For maintenance technicians, locating broken wire segments or loose connections is a time-consuming task, often necessitating the replacement of the entire harness.

| ![Harvester](/assets/img/projects/tdr-tractor/harvester.jpg){:.ioda} | ![Harvester](/assets/img/projects/tdr-tractor/harvester2.jpg){:.ioda} |

To address this challenge, I developed hardware that periodically performs **time-domain reflectometry (TDR)** measurements on multiple signal lines within the wire harness. TDR enables vehicle owners to visualize the impedance of the wires, making it possible to detect performance issues at specific locations. The hardware is installed between the vehicle’s main computer and the wire harness and is capable of isolating individual signal lines for measurement. The system automatically runs diagnostics during the vehicle’s startup and shutdown processes. Multiplexers are employed to switch between signal lines, directing them to the TDR measurement device. Measurements are stored in the cloud.
