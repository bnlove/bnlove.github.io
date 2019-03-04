---
layout: post
title: Slicing Spheres in Bricklayer to See Inside!
categories: [Programming 3D Artifacts]
tags: level4, 3D, sphere
author: Betty Love
---

#### Topics on this page
{:.no_toc}
* TOC
{:toc}

In this post we'll explore slicing spheres in order to see inside them.  For an introduction to spheres, check out [this post](/spheres).

Where you see this icon,
{% include image.html img="dot-bl.png"  alt=".bl icon"  %}
click on it to download the associated bricklayer program.

***

### Spheres inside spheres

What happens if we create a sphere inside a sphere in bricklayer?  Well, let's find out!
Let's start with a single sphere with radius 10.
{% include dotbl.html blfile="level4/sphere08.bl"  %}
```
sphere 10 [BLUE] (15,15,15);
```
{% include image.html img="level4/sphere10.png"  alt="Blue sphere with radius 10"  %}

Now let's put a smaller sphere at the same location (having the same center).  I'll give this one a radius of 7 and make it WHITE.
{% include dotbl.html blfile="level4/sphere09.bl"  %}
```
sphere 10 [BLUE]  (15,15,15);
sphere 7  [WHITE] (15,15,15);
```
{% include image.html img="level4/sphere10.png"  alt="Blue sphere with radius 10"  %}

Hmmm...where's the white sphere???  

We can't see it because it's inside the blue sphere.  I'm going to slice this artifact in half so we can see the middle.  How can I do that?  We need our old friend, the EMPTY block! I'll put an empty block over half of the sphere as follows.
{% include dotbl.html blfile="level4/sphere09.bl"  %}
```
sphere 10 [BLUE]  (15,15,15);
sphere 7  [WHITE] (15,15,15);
```
{% include image.html img="level4/sphere10.png"  alt="Blue sphere with radius 10"  %}


