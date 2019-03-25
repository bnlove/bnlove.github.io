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

Now let's put a smaller sphere at the same location (having the same center).  I'll give this one a radius of 7 and make it red.
{% include dotbl.html blfile="level4/sphere09.bl"  %}
```
sphere 10 [BLUE]  (15,15,15);
sphere  7 [RED]  (15,15,15);
```
{% include image.html img="level4/sphere10.png"  alt="Blue sphere with radius 10"  %}

Hmmm...where's the white sphere???  

### Circles inside circles

We can't see it because it's inside the blue sphere.  I'm going to slice this artifact in half so we can see the middle.  How can I do that? First we need to understand the location of the boundaries of the sphere. The image below shows a cross section of the sphere at its center. I created this in the bricklayer [Grid app](https://bricklayer.org/apps/grid_lite/grid.html), then marked it up on my ipad.  (I highly recommend using the Grid app to map out artifacts.) I did this analysis so that I could  come up with the coordinates of the yellow bounding square (which we'll use to create a yellow bounding box).  Note that I could have used trial and error, but some times it's difficult to know if you cut off part of a circle.  I also wanted to demonstrate this process.
{% include image.html img="level4/sphere11.jpg"  alt="Blue sphere with radius 10"  %}

Based on these calculations, we can write a Level_3 bricklayer program to create this.  You should look at each of the following commands and make sure you understand how to come up with the parameters used in each.
{% include dotbl.html blfile="level4/sphere10.bl"  %}

```
put2D (23,23) YELLOW (4,4);
put2D (21,21) EMPTY  (5,5);

circleXZ 10  BLUE  (15,15);
circleXZ  6  RED   (15,15);

put2D (1,1)   BLACK (15,15);
put2D (10,1)  WHITE (16,15);
```

Here's a look at the real artifact.  I put the white blocks in so that it's easier to confirm that the radius of the blue circle is 10 and the red circle is 6.
{% include image.html img="level4/sphere12.jpg"  alt="Blue sphere with radius 10"  %}

If I wanted to slice the circle in half and only see half of it, say the right half, then I can place a big empty block to cover the part that I don't want to be visible.  There's a bit of a problem with slicing the circle in _half_.  Can you think about what that problem is?  Hint: is the diameter of a circle even or odd?

Take a closer look at our artifact.
{% include image.html img="level4/sphere13.jpg"  alt="Radius 10, diameter 21"  %}
Our blue circle has radius 10, but its diameter is 21 because of the center block.  In general, we have the following relationship between the radius and diameter of a circle artifact:
> diameter = (2 x radius) + 1

Since 2 times any number is always even, adding 1 makes it odd, so the diameter of a circle in bricklayer is always odd.  What is half an odd number?  Not a whole number!  So what does half a circle mean?  One half will include the center point and one half will not.  For our purposes, I'll leave the center point in the half that will be displayed.

The following image shows my calculations for what size EMPTY block I need and where it needs to go.
{% include image.html img="level4/sphere14.jpg"  alt="Calculate dimensions and location of EMPTY block"  %}

I'll edit the code to remove the yellow frame and the left "half" of the circle. 
{% include dotbl.html blfile="level4/sphere11.bl"  %}
```
circleXZ 10  BLUE  (15,15);
circleXZ  6  RED   (15,15);

put2D (1,1)   BLACK (15,15);
put2D (10,1)  WHITE (16,15);

put2D (10,21) EMPTY (5,5);
```

Here's the artifact produced by this code.
{% include image.html img="level4/sphere15.png"  alt="Half a circle"  %}

### Back to spheres inside spheres

Now that we understand slicing a circle, we can extend that knowledge to slicing a sphere.  Let's go back to our red sphere inside a blue sphere. I'm going to add a set of axes to our artifact so that it's easier to get our bearings.  The following code generates the axes and our red sphere inside a blue sphere.  
{% include dotbl.html blfile="level4/sphere12.bl"  %}
```
put (30,1,1) WHITE  (0,0,0);   (* x axis *)
put (1,30,1) PINK   (0,0,0);   (* y axis *)
put (1,1,30) BLACK  (0,0,0);   (* z axis *)
put (1,1,1)  YELLOW (0,0,0);   (* origin *)


sphere 10  [BLUE]  (15,15,15);
sphere  7  [RED]   (15,15,15);
```
The resulting artifact is the following.
{% include image.html img="level4/sphere16.png"  alt="3D axes and spheres"  %}

There are many ways that we could slice the sphere in (almost) half (recall that the diameter of a sphere, just like that of a circle, is an odd number, so half of it is not a whole number). Let's first figure out how to chop off the left side. You can envision this as a knife slicing through the middle of the sphere from _z=0_ to _z=30_.  Although our sphere is not that big, we won't worry about that right now.  We'll just slice through some air!! The following image illustrates this idea. 
{% include image.html img="level4/sphere17.jpg"  alt="Slice sphere"  %}

Our approach will be to place a giant EMPTY block on the left side.  The center of the sphere in the _x_ direction (white axis) is at _x=15_. We need to back up one unit so that we don't chop off the layer of the sphere here.  Since our sphere is the only artifact we're working with, we don't have to be precise in determining the size of the EMPTY block.  The easy way is to locate the block at (0,0,0) and make it go to the build-space size in the _y_ and _z_ directions.  The only hard part is to figure out how far to go in the _x_ direction. Given our analysis above, we want to zap through _x=14_ which means our EMPTY block should be of size 15 in the _x_ direction.  Following is code that puts a giant YELLOW block there instead of EMPTY just to give a visual on what this block really looks like. 
{% include dotbl.html blfile="level4/sphere13.bl"  %}
```
sphere 10  [BLUE]  (15,15,15);
sphere  7  [RED]   (15,15,15);

put (15,30,30) YELLOW (0,0,0);  (* giant yellow block *)

(* place axes last *)
put (30,1,1) WHITE  (0,0,0);   (* x axis *)
put (1,30,1) PINK   (0,0,0);   (* y axis *)
put (1,1,30) BLACK  (0,0,0);   (* z axis *)
put (1,1,1)  YELLOW (0,0,0);   (* origin *)
```
The output is shown in the following image.
{% include image.html img="level4/sphere18.jpg"  alt="Slice sphere with giant yellow block"  %}

Note that we sliced it correctly since the sphere has radius 10 and we can see the 10 layers plus the center layer.  So now...let's put an EMPTY block there instead of YELLOW.  I also put a 1x1x1 white block at the center of the sphere just to make sure I wasn't chopping that layer off. 
{% include dotbl.html blfile="level4/sphere14.bl"  %}
```
sphere 10  [BLUE]  (15,15,15);
sphere  7  [RED]   (15,15,15);

put (1,1,1) WHITE (15,15,15);  (* white block at center *)

put (15,30,30) EMPTY (0,0,0);  (* giant empty block *)

(* place axes last *)
put (30,1,1) WHITE  (0,0,0);   (* x axis *)
put (1,30,1) PINK   (0,0,0);   (* y axis *)
put (1,1,30) BLACK  (0,0,0);   (* z axis *)
put (1,1,1)  YELLOW (0,0,0);   (* origin *)
```
The output is shown in the following image where we can see the cross-section of the red sphere inside the blue one as well as the white center block.
{% include image.html img="level4/sphere19.png"  alt="Slice sphere with giant empty block"  %}

### Slice horizontally (perpendicular to _y_ axis)

Suppose that instead of slicing vertically across the _x_ axis as we just did, we want to slice horizontally so that we can look down into the remaining "half".  Let's think about how to do that.
{% include image.html img="level4/sphere20.jpg"  alt="Slice sphere perpendicular to y axis"  %}

As the figure above shows, we want to empty out everything above the _y=15_ plane, i.e., everything above and including the _y=16_ plane. This means we need an EMPTY block that is size _(30,14,30)_ to go at location _(0,16,0)_.  Let's think about these values.  As shown in the image, we start the EMPTY block at _y=16_ and if we extend it to the maximum value of _y_, which is 29, then the EMPTY block needs to have height _14 = 29-16+1_.  The code is as follows. 
{% include dotbl.html blfile="level4/sphere15.bl"  %}
```
sphere 10  [BLUE]  (15,15,15);
sphere  7  [RED]   (15,15,15);

put (1,1,1) WHITE (15,15,15);  (* white block at center *)

put (30,14,30) EMPTY (0,16,0);  (* giant empty block *)

(* place axes last *)
put (30,1,1) WHITE  (0,0,0);   (* x axis *)
put (1,30,1) PINK   (0,0,0);   (* y axis *)
put (1,1,30) BLACK  (0,0,0);   (* z axis *)
put (1,1,1)  YELLOW (0,0,0);   (* origin *)
```
The resulting artifact follows.
{% include image.html img="level4/sphere21.png"  alt="Sliced sphere perpendicular to y axis"  %}

### Slice perpendicular to the _z_ axis
Now suppose we want to slice the sphere so that we can see the center when looking from the front (across the _x_ axis).  Consider the following image and think about what the size and location of the EMPTY block should be.
{% include image.html img="level4/sphere22.jpg"  alt="How to slic perpendicular to z axis"  %}

This is analogous to our first slice which took away the left part of the sphere when viewing from across the _x_ axis.  The code is as follows (compare it to the first slice).
{% include dotbl.html blfile="level4/sphere16.bl"  %}
```
sphere 10  [BLUE]  (15,15,15);
sphere  7  [RED]   (15,15,15);

put (1,1,1) WHITE (15,15,15);  (* white block at center *)

put (30,30,15) EMPTY (0,0,0);  (* giant empty block *)

(* place axes last *)
put (30,1,1) WHITE  (0,0,0);   (* x axis *)
put (1,30,1) PINK   (0,0,0);   (* y axis *)
put (1,1,30) BLACK  (0,0,0);   (* z axis *)
put (1,1,1)  YELLOW (0,0,0);   (* origin *)
```

The artifact produced is as follows.
{% include image.html img="level4/sphere23.png"  alt="Sliced sphere perpendicular to z axis"  %}








