---
layout: post
title: cGANs for Cartoon to Real life images
date: 2019-03-15
github_link: https://github.com/pranjalsrajput/Deep-Learning
description: Deep Learning Project
img: projects/cgans.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [GANs, Deep Learning]
---

## Problem Statement
This project aims to evaluate the robustness of thePix2Pix model by applying the Pix2Pix model to datasets consisting of cartoonized images. Using the Pix2Pix model, it should be possible to train the network to generate real-life images from the cartoonized images. The questions this project seeks to answer are:

Does the default set of hyper parameters of the original implementation work well on this cartoonized dataset?

Does the model properly recreate facial expressions and postures?

The project’s experiment attempts to explore the robustness of the multi-purpose Pix2Pix model. The problem is to determine whether, under the standard hyper-parameters, Pix2Pix can accurately recreate the facial features of the images in the original distribution based on cartoonized version of the images.

## Dataset
The dataset selected to train the Pix2Pix model is based on an adaption of the colorFERET facial image data.The colorFERET database contains 11337 images of faces in different angles and postures. These images are taken from 1199 individuals and are typically used for facial recognition research. The image data is provided in two versions: a higher resolution (512x768) and a lower resolution (256x384) version. In this project, the lower resolution version was used, in attempt to constrain the training duration.

<!-- ![I and My friends]({{site.baseurl}}/assets/img/we-in-rest.jpg) -->
