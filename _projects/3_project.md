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
    Approaches explored: domain randomization, kitchen images generated with GauGAN, more realistic simulated images, and small amounts of real-world data.
</div>
Observations from this project:

(a) We explored using a GAN to generate realistic textures from semantic masks. We trained GauGAN on the ADE20K dataset, but the model struggled to reproduce fine details with the available training data.

(b) We evaluated models trained on different data types using real images. In these experiments, adding just 1% of the real images improved detection results by 10%.

(c) An open question was how best to combine domain randomization, GAN-generated images, simulated images, and a small amount of real data to improve simulation-to-real transfer.


These notes document an exploratory project rather than an active release.
