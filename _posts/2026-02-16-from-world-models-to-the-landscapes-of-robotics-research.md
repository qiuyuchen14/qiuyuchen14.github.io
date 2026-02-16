---
layout: post
title: From World Models to the Landscapes of Robotics Research.
date: 2026-02-16 09:00:00
description: notes on where world models help in robotics, and where they do not.
---

Write down some thoughts to help me think in a bigger picture: how do world models fit into the current robotics landscape, when and how to use them, and when and why not to.

<span class="inline-subtitle">The Ultimate Debate</span>

A lot of robotics research is ultimately a bet around one thing: data. Real-world data collection is expensive, slow and hard to scale. Simulation becomes a natural bet.

OK, to me, an ideal/perfect simulator should model:

1. True **physics** of the real world: rigid body dynamics, deformation, force, friction, contact, thermal effects, compliance, internal stress, wear and tear.
2. True **visual** distribution of the real world: texture, lighting, shadows, camera noise, latency.
3. True **semantic** structure of the real world: realistic homes, object placement, scene logic.
4. True social **interaction** among agents: how humans and animals react, communicate, and follow norms.
5. True **causality** across timescales: milliseconds to years, from tiny defects to long-delayed failures.

If we have such a simulator, we would solve robotics. The reality is we are nowhere close to any of the points. 
For physics, although we have great simulators such as Isaac and Mujoco which can model rigid body dynamics under some assumptions, 
they struggle with fluid dynamics and complex contact. For perception, we have good rendering with Nvidia’s ray tracing, 
but it can never reach detailed visual distribution such as rich textures and shadows. 
For semantics, We are making great progress in real-to-sim, such as the recent SceneSmith, 
we are nowhere near modeling the full chaos and fine granularity of our world. 
For behaviors, we have networks that can predict human emotions, but modeling multi-agent behaviors or human–robot 
interaction dynamics still remains an open challenge. Finally, even humans have been doing weather forecasting for decades, 
and we only need to care about air and fluid dynamics. We can only predict like 7–10 days ahead of time, and the results are not usually accurate.

This also explains why physical AI is fundamentally hard, because robotics requires solving: physics, perception, common sense reasoning, behavior modeling and long-horizon modeling at the same time. Errors and noise in any of these layers can cause failure when robots operate in the real world. 

One pragmatic response is to abandon simulation and focus entirely on real-world data: figure out ways to collect large-scale data and train imitation policies directly in the real environment. (Pi, Sunday robotics, generalist etc).  However, scaling real-world data does not eliminate distributional shifts. When a purely reactive policy encounters an OOD state, recovery can be difficult. The policy maps states to actions based on training distribution, and it has no internal mechanism to evaluate alternative futures or reason about how to return to familiar regions of the state action space.

One approach is human-in-the-loop correction. When the robot deviates from expected trajectories, a human intervenes and provides additional demonstrations or corrective feedback (DAgger). Over time, this expands the coverage of the dataset and improves robustness, but this approach is still hard to scale. It still requires expensive supervision, and rare or catastrophic states may still remain underrepresented.

Conceptually, what is missing from a purely reactive policy is foresight. The robot needs some way to anticipate consequences before committing to them in the physical world, especially when mistakes could lead to costly or even fatal failures.


<span class="inline-subtitle">Entering the World Model</span>

Building such a simulator is almost impossible by hand, and that’s exactly the motivation of world models:
Can we “imagine” what happens by learning directly from real-world data?
Ideally, we want the world models to bridge parts of the sim2real gap. Rather than modeling physics, semantics, and behavior explicitly with math and equations (traditional simulators), we train a neural network to approximate:

`p(future | current_state, action)`

The “future” state can be represented in different ways, leading to different design choices and tradeoffs:

**1. Predicting frame by frame in the pixel space:**

such as Genie 3, world lab and DreamDojo, and often its used in:

1. Visual policy evaluation:

    (a) Evaluating Gemini Robotics Policies in a Veo World Simulator (2025)
   
    (b) WorldGym (Quevedo et al., 2025)

2. Data generation via imagination:

    (a) DreamGen (Jang et al., 2025) 

    (b) Ctrl-World (Guo et al., 2025)

3. Inference-time planning via generated rollouts:

   (a) Large Video Planner Enables Generalizable Robot Control (Chen et al, 2025): using video generation to imagine how humans do tasks and retarget to a robot.
   
    (b) Cosmos Policy (Kim et al., 2026)


Pros: keeps all perceptual information so its more expressive, easy to debug and evaluate, aligned well with vision-based policies

Cons: Computationally expensive and not great at long-horizon planning which is essential for robot tasks, visual info does not cover all physics info. 

(Inspired by Anirudha’s pointers from: https://x.com/Majumdar_Ani/status/2021242532517040560) 


**2. Predicting state and reward (Control-Oriented Latent Dynamics):**

such as Robotic World Model (Li, et.al, 2025), Dreamer-style models and classic model-based RL

These models learn a (sometimes latent) dynamics model: operate in  learned latent state or structured state space (joint positions, velocities, object states) and are typically used as a learned simulator to train a robot policy.

Pros: more efficient and potentially works for longer horizon tasks than pixel prediction, and its directly aligned with control

Cons: requires some well-defined state representation and usually less expressive, still doesn’t solve the model bias or exploitation issue. 


**3. latent state transitions such as JEPA, V-JEPA 2**

The goal is not to simulate for policy optimization, but to learn task-relevant, predictable structure while ignoring nuisance details like texture or lighting.

Pros: theoretically better for long-horizon and more efficient because the network does not need to waste so many parameters to capture non-relevant features

Cons: hard to evaluate, not straightforward for control dynamics 


**4. World Action Models (joint state-action generation)**


These models such as Dream zero (Jang et al., 2026) learn a joint distribution over trajectories, for both states and actions. So it approximates the world model as a robot policy. 

Pros: unifies world model and policy, make state more coherent with actions.

Cons: model bias directly translates into control errors


<span class="inline-subtitle">Tradeoff</span>

We want a model that maximizes: realism, stability, scalability, and long-horizon reasoning, 
but we cannot optimize all simultaneously. Frame to frame Pixel prediction maximizes visual realism and expressiveness, 
state models maximize control stability and efficiency, latent models maximize abstraction and scalability across time, 
WAM models maximize coherent state–action priors. No single representation dominates across all axes.


<span class="inline-subtitle">New Trend</span>
**Hybrid Systems** such as WorldVLA and RynnVLA-002: Instead of replacing policies, world models can be used selectively. Since world models are slow, a fast reactive policy can handle general tasks, but when the policy is uncertain or the system detects OOD states, it can ask world models and validate several actions. 

**Foundation-Style** World Models (UWM from Chuning): learn a broader joint distribution from heterogeneous data, which then can be used as a powerful backbone and can be used as a policy, or extract forward/inverse dynamics or do video prediction and so on. 


<span class="inline-subtitle">The Bigger Picture</span>

Imitation policies are highly sensitive to demonstration quality. 
Because they directly map states to actions, suboptimal or inconsistent demonstrations can degrade performance. 
In contrast, world models learn transition structure rather than behavioral optimality. 
Even failed or imperfect trajectories still provide useful information about how the environment responds to actions. 
As long as the dataset covers diverse state–action regions, world models can benefit from broader and noisier data.

World models exist because perfect simulation is impossible to design, and pure policy learning struggles with data efficiency and safety. 
However, world models also does not solve all the existing problems, but more like shifting the focus 
from modeling explicit physics errors to learned model bias, and from lacking supervision to managing uncertainty in imagination.

World models should not be viewed as oracles or standalone decision-makers, 
but as structured priors whose value although imperfect, might reduce search complexity in planning and policy learning  
(inspired by reading the article from Vikash: https://x.com/Vikashplus/status/2023388132415058277). 
The real question, then, is not whether world models are “better,” but where they can meaningfully reduce risk, cost, or uncertainty. 

In other words, If a world model does not reduce complexity somewhere, it is not adding value.

Many current demonstrations still focus on pick-and-place tasks, yet those are precisely the regimes where large 
VLA-style reactive policies already perform well. In short-horizon, well-covered settings, world models may add little marginal value. 
Their real leverage emerges when the policy is uncertain, when tasks demand longer-horizon reasoning, when consequences are costly or 
irreversible, or when systems need to escape local minima.  

