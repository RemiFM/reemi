---
layout: post
title: "Visual Odometry for Drone Navigation"
categories: project
tags: [AI, Drone]
---

## Hackathon
This weekend I participated in the **Battlefield of Things Hackathon - Drone Edition**. An event organised by the Belgian Defence for defence personnel, industry experts, drone enthusiasts, researchers and students. The event is a unique opportunity to work on drone hardware and software and tackle real-world challenges proposed by Belgian Defence.

One of the presented challenges was drone navigation in **GNSS- and RF- denied** regions, necessary due to advancements in jamming technologies. This made me think of the American [Theseus Drone](https://www.theseus.us/) which inspired me to approach the challenge in a similar way.

## Approach
Following methods could be used or combined to measure relative movement of the UAV:
- **IMU** - Accelerometer + Gyroscope + Magnetometer
- **Optical Flow** - A downwards facing camera tracks features, and calculates how the pixels are moved between frames. When the orientation and height above the surface is known, the absolure displacement can be calculated.
- **Stereo camera** - Using two downward facing camera's, accurate depth measurements and 3D perception can be created.
- **Sattelite imagery** - Sattelite images could be stored in the drone, and be compared to the video stream of the downward camera. This way, sensor drift from the methods above could be reduced.

| ![orangepi](/assets/img/projects/hackathon2/visual_odometry.png){:.ioda} |


## Result
I was not going to be able to tackle all this in just 24 hours, but I brought some hardware and started working. I used an Orange Pi 5 Plus SBC which has a Rockchip CPU and a 6Tops NPU. I also brought and implemented a OV13850 13MP camera module and a LSM9DS0 iMU module.

 | ![odometry](/assets/img/projects/hackathon2/visual_odometry.gif){:.ioda} |

I build a Flask webpage running on the SBC, and used OpenCV to recognize features in an image and track their relative movement between frames. From the GIF above it is clear that this tracking did not seem to work very well, and required more tuning (number of tracking points, feature treshold..) to improve it. Another difficulty was the depth/height estimation, as I did not have sensors for this, thus a constant height was assumed, not very accurate.

I had good fun creating this, even though the position estimation is far from reality. I might try to improve it at home, running more advanced SLAM algorithms which I hope do a better job than my own attempted 2D visual odometry.

More soon...maybe