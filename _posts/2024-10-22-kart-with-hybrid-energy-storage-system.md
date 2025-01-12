---
layout: post
category: test
---

By combining energy storage technologies with complementary features, we achieved a significantly extended driving range without sacrificing acceleration performance in a small electric vehicle.
 
A **semi-solid-state battery** uses a semi-solid electrolyte, offering higher energy density and improved safety compared to conventional batteries. The kart packs 6 kWh of energy in a compartment the size of a backpack, achieving an impressive energy density of 750 Wh/L or 350 Wh/kg. For this module I had to connect and configure a BMS system that would fit in the limited space available.
 
The **supercapacitor** module I developed has an energy capacity comparable to that of a smartphone, but can charge and discharge at a massive 24 kilowatts of continuous power. This fast power delivery is ideal for rapid acceleration. This module was completely custom designed and manufactured by me.

| ![kart](/assets/img/projects/hybrid-kart/kart2.jpeg){:.ioda} | ![kart](/assets/img/projects/hybrid-kart/kart1.jpeg){:.ioda} |

I created the electric and control architectures, and led both the hardware and software implementation. The main controller uses CAN to receive status information from both modules and uses an on-board network server to publish live data over UDP. A dashboard user interface with speed dial and vehicle information was created using Flask.

