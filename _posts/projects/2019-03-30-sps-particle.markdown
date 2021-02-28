---
layout: post
title: Localization and Activity Recognition App Using Particle Filters
date: 2019-03-30
github_link: https://github.com/pranjalsrajput/Smartphone-Sensing
description: Smartphone sensing project
img: projects/particleFilter.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Android Apps, Smartphone Sensing]
---

## Localization and Activity Recognition Apps
We developed applications for localization and activity recognition tasks, using KNNs, Bayesian filter and Particle filter. All the apps were test on Xiaomi Redmi 5A (Android 7.1.2, API 25).

### Using Particle Filters

* `Particle movement:` When a step is detected, every particle will make very small movements of p pixels for n times, where p is a small constant and n = stepsize/p. We have implemented it in such a way after realizing that moving the particles directly according to the step size will result in grid-like distribution of particles, which is undesirable. We used p= 2.

* `Movement constraints:` A particle violates the movement constraint if it fulfills any of the following conditions: (a) the pixel boundary of the particle intersects with the boundary of any wall; or (b) the pixel is located outside of the map.

* `Resampling:` When the particle violates the constraints, it is immediately resampled as it gets placed on top of a random surviving particle.

* `Determining location:` The location of the user is determined by calculating the particle density of every single cell. The cell with the highest density is the location of the user.

* `Results`
Following a unique path results in a convergence of the particle filter as the particles end up forming a cloud, as long as only proper 90 ◦ turns are taken while walking. After convergence, we went to every cell and the application was able to detect the correct cell location.

