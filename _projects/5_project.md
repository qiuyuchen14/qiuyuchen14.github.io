---
layout: page
title: Implicit Shape Augmentation
description: Generate novel shapes and ways to grasp them given minimal human demonstrations. 
img: assets/img/isagrasp.gif
importance: 5
category: work
---
Dexterous robotic hands have the capability to interact with a wide variety of household objects to perform tasks like grasping. However, learning robust real world grasping policies for arbitrary objects has proven challenging due to the difficulty of generating high quality training data. In this work, we propose a learning system (ISAGrasp) for leveraging a small number of human demonstrations to bootstrap the generation of a much larger dataset containing successful grasps on a variety of novel objects. Our key insight is to use a correspondence-aware implicit generative model to deform object meshes and demonstrated human grasps in order to generate a diverse dataset of novel objects and successful grasps for supervised learning, while maintaining semantic realism. We use this dataset to train a robust grasping policy in simulation which can be deployed in the real world. We demonstrate grasping performance with a four-fingered Allegro hand in both simulation and the real world, and show this method can handle entirely new semantic classes and achieve a 79% success rate on grasping unseen objects in the real world. 
Check out our [website](https://sites.google.com/view/implicitaugmentation/home)
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/isagrasp.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    An illustration of the training scheme in ISAGrasp. A few human demonstrations are provided from
motion capture. These demonstrations are retargeted to a four-fingered allegro robot in simulation. We use a
correspondence-aware generative model to extrapolate the retargeted demonstrations to a large dataset of novel
objects. We use this dataset to train a single grasping policy that is able to generalize to a variety of unseen
objects in simulation and real world.
</div>

<div style="text-align: center;">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/isagrasp.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    ISAGrasp significantly improves the generalization ability to unseen objects. We evaluated our policy on 22 unseen objects in real world and achieve 79% success rate.
</div>
