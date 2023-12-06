---
title: "Fitting Homographies"
date: 2023-11-12T15:20:42-07:00
draft: false
---

Fitting an image homography was one of the first projects I ever built when learning computer vision, and so I thought I'd take a bit of a step back and document it.

## Expected Prior Knowledge
If you aren't familiar with the term linear map or linear transformation, or the idea of an SVD, I would suggest keeping a good resource on Linear Algbra nearby as you read through this post. We'll be going kinda deep, and assume some linear algebra knowledge. ChatGPT also isn't bad at linear algebra, so that might be a good place to look. **Definitely keep reading, even if you don't know Linear Algebra!**

## What's the aim?

Formally, an **image homography** is a linear map(linear transformation, matrix, or more simply a function) that maps points from one image onto another image. It has applications in pose estimation, SLAM, making panoramas, etc.

It's always best to see a visual of what our aim is, so here you go:

```py
import numpy as np

```
