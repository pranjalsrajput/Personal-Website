---
layout: post
title: Custom Dataloaders for Vision and NLP tasks in PyTorch 
date: 2020-08-24
description: Custom Dataloaders for Vision and NLP tasks in PyTorch 
img: blogs/dataloader.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [pytorch, machine learning]
---

This post is an effort to understand how dataloaders in Pytorch work and thereafter we will write our own dataloaders for vision as well as vision + language tasks.

Having worked with Pytorch[1] for a while, I can safely say that it is my framework of choice for deep learning (DL) tasks given its simplicity to understand, code and especially debug. Data loading is first step for any DL project. Let's work through step-by-step the data-loading process with Pytorch dataloader.



