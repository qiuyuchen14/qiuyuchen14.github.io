---
layout: page
title: Residual RL
description: Can a better action representation help an RL policy learn from fewer samples?
img: assets/img/residual_RL/data2.gif
importance: 2
category: work
---
This is a [RL class](https://homes.cs.washington.edu/~bboots/RL-Fall2020/) project with Xiangyun Meng and [Mohit Shridhar](https://mohitshridhar.com/).

We explored whether residual reinforcement learning could refine human demonstrations in simulation. Reducing the action space with principal component analysis (PCA) preserved useful behavior from the demonstrations while helping the policy learn smoother trajectory refinements from fewer samples.

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
    Grasping trajectories refined with residual RL succeeded where replaying human demonstrations failed because of tracking and inverse kinematics errors.
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
