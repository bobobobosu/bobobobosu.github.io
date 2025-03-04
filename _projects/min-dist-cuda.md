---
layout: page
title: CUDA-Accelerated Minimum Distance Query
description: Minimum distance with gradient among massive number of meshes using CUDA
img: assets/img/project_MCD/header.png
importance: 3
category: work
---

# Parallel Minimum Distance Query Among Convex Meshes

This project presents a parallel approach to measure the closest distance between 3D convex shapes, an important task in computer graphics and robotics. The CUDA implementation of GJK algorithm achieved a 20x speedup over the CPU implementation with the same scene.

## Real-World Application

This project is the default minimum distance query implementation in [CFSTrajOpt.jl](https://github.com/bobobobosu/CFSTrajOpt.jl/blob/master/mcd/mcd.cu), where it enables real-time collision avoidance and motion planning by efficiently computing distances between robot links and environmental obstacles.



<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        <iframe src="{{ site.baseurl }}/assets/pdf/min-dist-cuda/poster.pdf" width="100%" height="600" frameborder="0" allowfullscreen></iframe>
    </div>
</div>
<div class="caption">
    Overview of the CUDA-accelerated minimum distance query implementation.
</div>


## Technical Report

For more detailed information about the implementation and performance analysis, please refer to the technical report:

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        <a href="/assets/pdf/min-dist-cuda/report.pdf" target="_blank">
            <button class="btn btn-primary">View Implementation Details</button>
        </a>
    </div>
</div>