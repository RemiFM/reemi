---
layout: post
title: "Low-Cost Tethered Drone"
categories: project
tags: [drones, power]
---


Tethered drones are a good solution for applications requiring long-duration flight, consistent power delivery, and secure communication. Unlike traditional drones that rely on onboard batteries, tethered drones are connected to a ground station via a physical tether, enabling **continuous operation while maintaining a secure and interference-resistant data link**. These systems are increasingly popular in security and surveillance applications, offering real-time aerial monitoring without the risk of signal interception or limited flight time.

| ![kart](/assets/img/projects/tethered-drone/tethered-drone.png){:.ioda} |

In a recent project, I explored **low-cost solutions** for tethered drones by looking into different electrical architectures. The goal was to determine the feasibility of drone systems that provide reliable power and communication while maintaining affordability and scalability for diverse use cases. In particular we compared both **AC tether** systems and **high voltage DC tether** systems, in both centralized and distributed power topologies. I created PCB modules for the different topologies. Communication signals were transmitted over the same lines used to deliver power, utilizing **signal superposition** to combine both functionalities within a single tether.

| ![PCB](/assets/img/pcb/pcb-acdc-700W.png){:.ioda} |
| ![PCB](/assets/img/pcb/pcb-vicor-bus-converter.jpg){:.ioda} |
