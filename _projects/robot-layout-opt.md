---
layout: page
title: Robot Layout Optimization
description: Workload-driven warehouse layout optimization
img: assets/img/project_Layout/header.png
importance: 1
category: work
---

In modern manufacturing, the physical arrangement of robots within a production line can dramatically impact both efficiency and energy consumption. Even small layout improvements can lead to significant cost savings at scale. Our research addresses this challenge with an innovative approach called Multi-Robot Layout Optimization (MRLO).
<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_Layout/header.png" title="MRLO Framework" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The Multi-Robot Layout Optimization Framework (MRLO) runs in a loop with global optimization and local optimization. The global optimization phase uses an evolutionary algorithm to establish preliminary robot layout, which are then refined at the lower level.
</div>

## The Challenge of Robot Layout Design

Determining the optimal placement of robots in a production environment is surprisingly complex. The layout affects how robots coordinate with each other, how they navigate around physical constraints, and how efficiently they can complete their assigned tasks.

Poor robot positioning creates unnecessary bottlenecks. For example, in a dual-robot assembly line, if Robot A feeds parts to Robot B but they're poorly positioned relative to each other, one robot might need to wait for the other to complete its motion before proceeding, even when their tasks could theoretically overlap.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/project_Layout/two-robot-pipeline.png" title="Two-Robot Pipeline" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/project_Layout/two-robot-petri-model.png" title="Petri Net Model" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: A Two-Robot Sequential pipeline with one conveyor. Right: The corresponding Petri Net model representing workflow dependencies.
</div>

## Our Approach: The MRLO Framework

The Multi-Robot Layout Optimization (MRLO) framework tackles these challenges through a sophisticated two-level optimization approach:

1. **Global Optimization**: Uses an evolutionary algorithm called Covariance Matrix Adaptation Evolution Strategy (CMA-ES) to efficiently search through possible robot layouts

2. **Local Optimization**: For each candidate layout, quickly refines the solution through:
   - Layout temporal optimization to find time-optimal trajectories
   - Workflow scheduling to determine optimal task timing
   - Energy optimization to reduce power consumption while maintaining cycle time

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_Layout/local-opt.png" title="Local Optimization Process" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    An example of local optimization process on a Two-Robot pipeline with conveyors. It consists of three steps: (1) Layout Temporal Optimization, (2) Workflow Scheduling, and (3) Energy Optimization.
</div>

## Key Innovations

Our work bridges the gap between robot-centric and workflow-centric approaches through three key innovations:

1. **Integrated layout and trajectory planning**: Rather than treating robot placement and motion as separate problems, MRLO allows robots to adapt their trajectories based on their relative positions.

2. **Explicit payload dynamics modeling**: The framework accounts for how carried objects affect robot performance, ensuring that layouts work well with actual payloads.

3. **Two-level optimization**: By combining global layout exploration with local trajectory refinement, the approach significantly speeds up the search process while finding high-quality solutions.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_Layout/results-plot.png" title="Optimization Results" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Layout optimization results showing the trade-off between energy and cycle time found by the CMA-ES global optimization. Even with only local optimization using Expert Layout as initial guess, significant improvement can be seen in cycle time and energy consumption.
</div>

## Intelligent Workflow Scheduling

One of the most impressive aspects of MRLO is its workflow scheduling component. Using a Petri net model of the production system, it not only determines when tasks should execute but also identifies which motions are on the critical path (those that directly affect cycle time) and which have timing flexibility.

This understanding enables a smart energy optimization phase where non-critical motions can be selectively slowed down to reduce energy consumption without affecting overall cycle time. The framework can also prioritize layouts that favor critical motions, leading to better overall efficiency.

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/project_Layout/robot-results.png" title="Layout Results" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Results from optimizing a robot assembly line, showing the improved layout and performance metrics before and after optimization.
</div>

## Results That Matter

We demonstrated MRLO's effectiveness through simulations of different production scenarios, including a two-robot sequential pipeline with conveyors and a parallel robot assembly line. The results showed substantial improvements in both cycle time and energy consumption compared to baseline approaches.

Even more impressive, these improvements were achieved with significantly fewer iterations than traditional methods, highlighting the efficiency of the two-level optimization approach.

As manufacturing continues to automate, optimizing robot layouts becomes increasingly important for maximizing productivity and minimizing energy consumption. The MRLO framework provides a powerful new tool for addressing this challenge, with potential applications in numerous industries from automotive manufacturing to electronics assembly.