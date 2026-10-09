---
layout: page
title: Sim2Real
description: An earlier exploration of generative image translation for simulation-to-real transfer.
img: assets/img/sim2real/sim2real.png
importance: 3
category: work
---
This earlier project explored whether generative adversarial networks (GANs) could make simulated images more realistic for robot perception. We compared domain randomization, generated images, and small amounts of real-world data to investigate the gap between simulation and real environments.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/sim2real/sim2real.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Different approaches are investigated in this project. (1) domain randomization (2) Generated kitchen example using GauGAN (3) making synthetic images more realistic inside a simulator (4) inject only a small amount of real world data. 
</div>
Observations from this project:

(a) Our goal is that given an image with semantic masks, we can use GAN to "fill" textures so that it will look realistic.
 We found that GAN couldn't generate very great images with fine details with the scales of the current dataset. We trained GauGAN on the ADE20K dataset. Because the training samples are not huge, the network couldn't effectively learn
expressive features that lead to good reconstructed images. 

(b) We evaluated different data types on real images. We found that by injecting even only 1% of the real images could improve detection results by 10%

(c) how can we use domain randomization, GAN images, sim images, and a little real images, train a network that could better at sim to real transfer. 


These notes document an exploratory project rather than an active release.