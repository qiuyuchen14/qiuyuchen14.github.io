---
layout: page
title: Residual RL 
description: Can we train a more sample efficient RL policy using a better action representation?
img: assets/img/residual_RL/data2.gif
importance: 2
category: work
---
This is a [RL class](https://homes.cs.washington.edu/~bboots/RL-Fall2020/) project with [Xiangyun Meng](https://homes.cs.washington.edu/~xiangyun/) and [Mohit Shridhar](https://mohitshridhar.com/)

In this work, we explored if we can improve human demonstrations in simulation using residual reinforcement learning. Our key insight is that by reducing action space via PCA, we can dramatically 
reduce the high sampling complexity, while preserving behavior features from the demonstrations, which leads to a more sample efficient and smooth trajectory refinement. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/residual_RL/data2.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/residual_RL/data3.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/residual_RL/data36.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/residual_RL/data64.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/residual_RL/data93.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/residual_RL/data198.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/residual_RL/data231.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/residual_RL/data46.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    Successful refined grasping trajectories by residual RL, while replaying human demonstrations would fail due to tracking error and IK error. 
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/residual_RL/comparison_pca.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/residual_RL/qualatative.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>