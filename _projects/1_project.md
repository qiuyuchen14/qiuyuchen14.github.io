---
layout: page
title: Dexterous Grasping
description: Can a robot learn from humans with only a few examples?
img: assets/img/robot.gif
importance: 1
category: work
---
Teaching a multi-fingered dexterous robot to grasp objects in the real world has been a challenging problem due to 
its high dimensional state and action space. We propose a robot-learning system that can take a small number of 
human demonstrations and learn to grasp unseen object poses given partially occluded observations. Our system 
leverages a small motion capture dataset and generates a large dataset with diverse and successful trajectories 
for a multi-fingered robot gripper. By adding domain randomization, we show that our dataset provides robust 
grasping trajectories that can be transferred to a policy learner. We train a dexterous grasping policy that 
takes the point clouds of the object as input and predicts continuous actions to grasp objects from different 
initial robot states. We evaluate the effectiveness of our system on a 22-DoF floating Allegro Hand in simulation 
and a 23-DoF Allegro robot hand with a KUKA arm in the real world. The policy learned from our dataset can 
generalize well on unseen object poses in both simulation and the real world.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/human_demos.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/simulation.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/robot.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Human demonstrations. Middle: Policy on unseen poses. Right: Policy deployed on a robot. 
</div>

Details are coming soon!