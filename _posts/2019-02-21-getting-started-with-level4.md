---
layout: post
title: Getting Started with Bricklayer Level 4
categories: [Getting Started]
tags: featured
author: Betty Love
---

#### Topics on this page
{:.no_toc}
* TOC
{:toc}

Level 4 in Bricklayer opens up the world of 3D artifacts!  To create and run a Level_4 program, you must use the Bricklayer app (not Bricklayer-Lite).  For an introduction to programming in the Bricklayer app, check out [this post](/getting-started-with-bricklayer).

***

### Coordinates in 3D space

Let's start with a review of 2D coordinates in Bricklayer.  When programming in 2D, artifacts are placed in the x-z plane.  The point (x,z) is x units in the horizontal direction from 0 and z units in the vertical direction from 0.  Consider the figure below.

{% include image.html img="level4/level4-01.jpg"  alt="Horizontal and vertical coordinates"  %}

As we move to 3D, we (visually) lay the x-z plane flat, so the above artifact would be viewed as follows.

{% include image.html img="level4/level4-02.jpg"  alt="x-z plane laid flat"  %}

We think of x as the *width* of the artifact and z as the *depth*.  The third dimension, which we'll label as *y*, is the height.  In the artifact above, the height is one.  Below is the same artifact with second layer the same size as the first added.

{% include image.html img="level4/level4-03.jpg"  alt="3D artifact"  %}

The code to create this artifact is shown below.

{% include image.html img="level4/level4-04.png"  alt="Code for 3D artifact"  %}
