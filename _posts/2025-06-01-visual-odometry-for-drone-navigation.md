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

More soon...    maybe!







<h1>Lissajous</h1>

<div class="controls">
<div class="control">
<label>Amplitude X: <span id="ampAVal">100</span></label>
<input type="range" id="ampA" min="10" max="300" value="100">
</div>
<div class="control">
<label>Amplitude Y: <span id="ampBVal">100</span></label>
<input type="range" id="ampB" min="10" max="300" value="100">
</div>
<div class="control">
<label>Frequency X: <span id="freqAVal">3</span></label>
<input type="range" id="freqA" min="1" max="10" value="3">
</div>
<div class="control">
<label>Frequency Y: <span id="freqBVal">2</span></label>
<input type="range" id="freqB" min="1" max="10" value="2">
</div>
<div class="control">
<label>Phase δ (deg): <span id="phaseVal">0</span></label>
<input type="range" id="phase" min="-360" max="360" value="0">
</div>
</div>

<canvas id="canvas" width="600" height="600"></canvas>

<script>
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");

  const ampA = document.getElementById("ampA");
  const ampB = document.getElementById("ampB");
  const freqA = document.getElementById("freqA");
  const freqB = document.getElementById("freqB");
  const phaseSpeedSlider = document.getElementById("phase");
  const phaseVal = document.getElementById("phaseVal");

  const ampAVal = document.getElementById("ampAVal");
  const ampBVal = document.getElementById("ampBVal");
  const freqAVal = document.getElementById("freqAVal");
  const freqBVal = document.getElementById("freqBVal");

  let phaseDeg = 0;
  let lastTime = performance.now();

  function drawLissajous(phaseRadians) {
	const A = parseFloat(ampA.value);
	const B = parseFloat(ampB.value);
	const a = parseFloat(freqA.value);
	const b = parseFloat(freqB.value);

	ampAVal.textContent = A;
	ampBVal.textContent = B;
	freqAVal.textContent = a;
	freqBVal.textContent = b;
	phaseVal.textContent = phaseSpeedSlider.value;

	ctx.clearRect(0, 0, canvas.width, canvas.height);
	ctx.beginPath();

	const centerX = canvas.width / 2;
	const centerY = canvas.height / 2;
	const steps = 1000;
	const tMax = 2 * Math.PI;

	for (let i = 0; i <= steps; i++) {
	  const t = tMax * i / steps;
	  const x = A * Math.sin(a * t + phaseRadians);
	  const y = B * Math.sin(b * t);
	  const canvasX = centerX + x;
	  const canvasY = centerY - y;

	  if (i === 0) {
		ctx.moveTo(canvasX, canvasY);
	  } else {
		ctx.lineTo(canvasX, canvasY);
	  }
	}

	const my_gradient = ctx.createRadialGradient(centerX, centerX, 0, Math.max(canvas.width, canvas.height), canvas.height, canvas.height);
	my_gradient.addColorStop(0, "magenta");
	my_gradient.addColorStop(0.5, "blue");
	my_gradient.addColorStop(1, "red");

	ctx.strokeStyle = my_gradient;//"#007acc";
	ctx.lineWidth = 5;
	ctx.stroke();
  }

  function animate(now) {
	const deltaTime = (now - lastTime) / 1000; // seconds
	lastTime = now;

	const speedDegPerSec = parseFloat(phaseSpeedSlider.value);
	phaseDeg = (phaseDeg + speedDegPerSec * deltaTime) % 360;
	const phaseRad = phaseDeg * Math.PI / 180;

	drawLissajous(phaseRad);
	requestAnimationFrame(animate);
  }

  // Update drawing when sliders change (except phase slider, which is now speed)
  [ampA, ampB, freqA, freqB].forEach(slider => {
	slider.addEventListener("input", () => drawLissajous(phaseDeg * Math.PI / 180));
  });

  // Start animation
  requestAnimationFrame(animate);
</script>





