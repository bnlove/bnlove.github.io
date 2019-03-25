---
layout: post
title: Rings and Cylinders
categories: [Programming 3D Artifacts]
tags: level4, 3D, cylinder, ring, ringX, ringY, ringZ, level 4, level_4, hollowCylinder
author: Betty Love
---

#### Topics on this page
{:.no_toc}
* TOC
{:toc}

In this post we'll investigate how to create rings and cylinders in Bricklayer Level_4.  For an introduction to Level_4 programming, check out [this post](/getting-started-with-level4).

Where you see this icon,
{% include image.html img="dot-bl.png"  alt=".bl icon"  %}
click on it to download the associated bricklayer program.

***

### Level_4 Documentation

The official documentation for Level_4 functions is found on the [bricklayer website](https://bricklayer.org) by selecting Apps -> Bricklayer -> Level 4 Document or through this [direct link](https://bricklayer.org/level-4-document/). 

### Rings in 2D
Before discussing 3D rings, let's review the idea of a ring in 2D. A ring is defined by its radius, thickness, color, and location.  These are the parameters for the _ringXZ_ function. Consider the following code in Level_3 and its output.
{% include dotbl.html blfile="level4/ringX01.bl"  %}
```
(* ringXZ radius thickness color location *)
ringXZ 10  1  BLUE  (15,25);
ringXZ 10  4  RED   (40,25);
ringXZ 20 10  GREEN (75,25);
```
{% include image.html img="level4/ring01.png"  alt="Rings in Level_3"  %}


### Rings in 3D
Rings in 3D are analogous to rings in 2D with one exception: the length of the ring.  Essentially rings in 3D are cylinders.  To create a cylinder, we need to know its radius, thickness (of its walls), color, and location.  But we also need to know its orientation: is it standing up?  laying down? laying down front to back or side to side?  