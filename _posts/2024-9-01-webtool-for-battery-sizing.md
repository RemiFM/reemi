---
layout: post
category: test
---

Hybrid Battery Energy Storage Systems (HBESS) combine two distinct but complementary cell technologies in a single battery solution. For example, a battery cell technology with a high energy density like NMC could be combined with a battery cell technology with high power density like LTO. In this way, a sort of 'composite' battery storage can be created which has the benefits of both cell technologies used.

| ![kart](/assets/img/projects/sizing-tool/sizing-tool2.png){:.ioda} | ![kart](/assets/img/projects/sizing-tool/sizing-tool1.png){:.ioda} |

More difficult becomes the sizing and control of such hybrid battery systems. At what times will you use the "High Energy" cells, and at what times do you use the "High Power". Using the [CasADi](https://web.casadi.org/) framework non-linear optimization within Python, I created a web tool which can be used to design an optimal hybrid battery system, minimizing either the total cost, volume or weight. The webtool is created using the Streamlit framework, and is hosted using Azure.

The tool makes clear what theoritical benefits hybrid battery solutions can bring for demanding applications like maritime, construction and transportation.

>The tool is available on [battery.flandersmake.be](http://battery.flandersmake.be).


