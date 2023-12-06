---
title: "What are neural radiance fields?"
date: 2023-10-04T15:50:45-07:00
draft: true
---

## They're everywhere
Seemingly out of nowhere, Neural Radiance Fields have taken the world of computer vision by storm. They have an impressive ability to learn the geometry of a scene, and their ability to render novel views of a world given a small set of inputs is rather remarkable. Just looking at the work of Waymo in Block-NeRF motivates this well enough; given images from a self-driving car, they are able to model and synthesize the world accurately from views that no car could ever go to. 

In this post, I hope to keep a running list of advancements in the field, noting everyone's contributions and helping break down what's going on here. 

{{< youtube 6lGMCAzBzOQ >}}

## The Original NeRF
The original NeRF, or Neural Radiance Field, was proposed by Mildenhall et al. in 2020 and started the recent explosion in this research area. This paper lays out the basic idea behind NeRFs, and is fundamental to understand before moving forward.

### High Level Overview
At a high level, the original NeRF does the same thing all NeRFs do; **given a point in 3D space, predict the color and volume density at that point**. This might sound weird, since it has nothing to do with predicting images or anything of that sort. And that is something I wish to clarify right now; Neural Radiance Fields have no notion of images, only points in space

So how do Neural Radiance Fields generate images? That is done by using techniques from volume rendering that **predict the color at an image pixel by rendering color along the viewing ray of the pixel**.

To get a good visual interpretation of this, we can look at a nice visualization given by {{< person url="https://www.matthewtancik.com/" name="Matthew Tancik" nick="tancik" text="Original NeRF author" picture="https://avatars.githubusercontent.com/u/3310961?v=4" >}}
 alongside the original NeRF.

{{<raw>}}
<iframe width="100%" height="450" src="https://www.youtube.com/embed/JuH79E8rdKc?si=F_W7eRYD-Q7nnJ3v&amp;start=9" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
{{</raw>}}

### Model and Inference
As mentioned in the above video, the model takes in a 