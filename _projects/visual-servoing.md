---
layout: page
title: Visual Servoing a Microscope with MRAC
description: Visual Servoing a Microscope with Model Reference Adaptive Control (MRAC)
img: assets/img/project_MRAC/header.png
importance: 2
category: work
related_publications: true
---



<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="https://www.youtube.com/embed/0meslhCgdzU" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## Project Overview

This project addresses the challenge of precisely controlling a DIY microscope using visual servoing with Model Reference Adaptive Control (MRAC). The system consists of a motorized XY stage with a webcam for feedback. The primary technical challenge is that the stage's kinematics and dynamics are unknown and constantly changing, making traditional fixed-parameter control methods ineffective.

### Technical Approach

Visual servoing uses visual feedback from a camera to control the motion of a robot. In this system, I implemented:

1. **Computer Vision Pipeline**: Real-time image processing to detect and track microscopic features
2. **Model Reference Adaptive Control**: An advanced control strategy that:
   - Estimates unknown system parameters online
   - Adapts to changing dynamics during operation
   - Maintains consistent performance despite uncertainties

The MRAC controller continuously updates its internal model based on the error between desired and actual motion, allowing it to learn and compensate for the system's unknown characteristics without prior calibration.

### Results

This approach achieved positioning accuracy of approximately 40 microns, enabling precise microscope navigation for biological sample inspection. The system demonstrates robust performance despite:

- Manufacturing imperfections in the stage
- Nonlinear friction effects
- Changing system parameters over time

### Implementation Details

The control system runs on a standard laptop connected to stepper motor drivers. The vision processing pipeline extracts feature positions from webcam images at 30 fps, providing position feedback to the adaptive controller.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/project_MRAC/header.png" title="System Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    System architecture of the visual servoing microscope with Model Reference Adaptive Control (MRAC).
</div>