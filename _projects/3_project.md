---
layout: page
title: Sim2Real
description: Can we leverage the power of generative models and solve a long-standing issue in robotics?
img: assets/img/sim2real/sim2real.png
importance: 3
category: work
---
For decades, robotics has been facing a crucial issue: sim2real transfer. Collecting data in real world is very expensive,
therefore, leveraging a simulator to provide infinite synthetic data seems to be a powerful approach. However transfering 
policies trained in simulation to real world is not trivial. A lot of work in the past has been focusing on this direction including
domain randomization, close-loop policy with real world feedback, or learning more semantic features beyond RGBD images. In this work, 
we are trying to explore the possibility to use recent progress in GAN, and generate realistic images from synthetic images in a 
simulator, in order to close the gap between sim to real. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/sim2real/sim2real.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Different approaches are investigated in this project. (1) domain randomization (2) Generated kitchen example using GauGAN (3) making synthetic images more realistic inside a simulator (4) inject only a small amount of real world data. 
</div>
While project is not complete yet, many interesting observations deserve further investigation. 

(a) Our goal is that given an image with semantic masks, we can use GAN to "fill" textures so that it will look realistic.
 We found that GAN couldn't generate very great images with fine details with the scales of the current dataset. We train GaoGAN on ADE20K dataset. Because the training samples are not huge, the network couldn't effectively learn
expressive features that lead to good reconstructed images. 

(b) We evaluated different data types on real images. We found that by injecting even only 1% of the real images could improve detection results by 10%

(c) ...


More details are coming soon!