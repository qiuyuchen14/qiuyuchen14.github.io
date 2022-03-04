---
layout: page
title: Medical Images Analysis
description: Reconstruction of blood vessels from stereo x-ray images
img: assets/img/medical_img/demonstration.png
importance: 3
category: work
---
We propose a fully automatic system to reconstruct and
visualize 3D blood vessels in Augmented Reality (AR) system from stereo X-ray images with bones and body fat. Currently, typical 3D imaging technologies are expensive and
carrying the risk of irradiation exposure. To reduce the potential harm, we only need to take two X-ray images before
visualizing the vessels. Our system can effectively reconstruct and visualize vessels in following steps. We first conduct initial segmentation using Markov Random Field and
then refine segmentation in an entropy based post-process.
We parse the segmented vessels by extracting their centerlines and generating trees. We propose a coarse-to-fine
scheme for stereo matching, including initial matching using affine transform and dense matching using Hungarian
algorithm guided by Gaussian regression. Finally, we render and visualize the reconstructed model in a HoloLens
based AR system, which can essentially change the way
of visualizing medical data. We have evaluated its performance by using synthetic and real stereo X-ray images, and
achieved satisfactory quantitative and qualitative results.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/medical_img/master_thesis_system.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    System overview
</div>

Check out our [paper](https://openaccess.thecvf.com/content_ICCV_2017_workshops/papers/w1/Chen_Virtual_Blood_Vessels_ICCV_2017_paper.pdf)