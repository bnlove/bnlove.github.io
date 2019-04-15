---
layout: post
title: A function to create a wire-frame box
categories: [Functions]
tags: level4, functions
author: Betty Love
---

#### Topics on this page
{:.notoc}
* TOC
{:toc}

In this post we'll write a function for creating a wire-frame box like this one.
{% include image.html img="functions/wireFrameBox08.png"  alt="Wire-frame box"  %}

Where you see this icon,
{% include image.html img="dot-bl.png"  alt=".bl icon"  %}
click on it to download the associated bricklayer program.

***

### Wire-frame box function

Our function will include parameters to control the size of the box (_xSize_,_ySize_,_zSize_), the color of the box (_color_), and the location of the box (_x_,_y_,_z_).  To create our wire-frame box, we will first create a solid box, then use _EMPTY_ blocks to hollow out what we don't want to keep.  Our progression will be as shown in the following figure.  The red and yellow blocks are added to provide reference points. 

{% include image.html img="functions/wireFrameBox07.png"  alt="Wire-frame box sequence"  %}

Only four _put_ function calls are needed to create a wire-frame box.  The general form of the function is as follows:
```
fun wireFrameBox (xSize,ySize,zSize,x,y,z,color) = 
(
(*
    put ...  <--- create solid box 
    put ...  <--- empty box from front to back 
    put ...  <--- empty box from left to right 
    put ...  <--- empty box vertically
*)
);
```

The following code to place the red and yellow bricks for reference will also be included in the function, but will not be displayed henceforth in order to not detract from the main four _put_ calls.

```
(* Place red and yellow bricks for reference *)
    put (1,1,1) RED    (x,y,z);
    put (1,1,1) YELLOW (x+xSize-1,y+ySize-1,z+zSize-1)
```

#### Step 1: make solid box 

Creating the initial solid box is the easiest step since we are given all the parameters we need for the corresponding _put_ function call. 
{% include dotbl.html blfile="functions/wireFrameBox01.bl"  %}
```
fun wireFrameBox (xSize,ySize,zSize,x,y,z,color) = 
(
    put (xSize,ySize,zSize) color (x,y,z);
(*
    put ...  <--- empty box from front to back 
    put ...  <--- empty box from left to right 
    put ...  <--- empty box vertically
*)
);
```
The function call
```
wireFrameBox (14, 5, 10, 0, 0, 0, BLUE);
```
produces the following artifact.
{% include image.html img="functions/wireFrameBox01.png"  alt="Solid block"  %}


#### Step 2: empty box from front to back

In this step we will determine the dimensions and location of the _put EMPTY_ call we need in order to empty the box from front to back.  Consider the figure below.
{% include image.html img="functions/wireFrameBox03.jpg"  alt="Empty front to back"  %}
The green rectangle marks the area  of the box that we want to remove all the way from front to back.  Since we want to leave the left and right sides of the box, the _x-dimension_ of the section to remove is _xSize-2_.  Similarly, since we want to leave the top and bottom of the box, the _y-dimension_ of the section to remove is _ySize-2_. And finally, since we want to remove this section from the front of the box to the back, the _z-dimension_ of the section to remove is the full _zSize_.

So at this point we know the code we need looks like the following:
```
put (xSize-2,ySize-2,zSize) EMPTY (?, ?, ?)
```
We need to figure out the reference point (location) of this EMPTY block. As is shown in the figure above, the lower left corner of the green rectangle is one over and one up from the red block while the _z_ coordinate is the same as that of the red block.  Adding this to our _put_ call and inserting it into the function gives us this:
```
fun wireFrameBox (xSize,ySize,zSize,x,y,z,color) = 
(
    put (xSize,ySize,zSize) color (x,y,z);
    put (xSize-2,ySize-2,zSize) EMPTY (x+1,y+1,z)
);
```
The function call
```
wireFrameBox (14, 5, 10, 0, 0, 0, BLUE);
```
produces the following artifact.

{% include image.html img="functions/wireFrameBox04.png"  alt="Emptied front to back"  %}

#### Step 3: empty box from left to right

In this step we will determine the dimensions and location of the _put EMPTY_ call we need in order to empty the box from left to right.  Consider the figure below.
{% include image.html img="functions/wireFrameBox08.jpg"  alt="Empty left to right"  %}
The green rectangle marks the area  of the box that we want to remove all the way from left to right.  Since we want to leave the front and back frames of the box, the _z-dimension_ of the section to remove is _zSize-2_.  Similarly, since we want to leave the top and bottom of the box, the _y-dimension_ of the section to remove is _ySize-2_. And finally, since we want to remove this section from the left of the box to the right, the _x-dimension_ of the section to remove is the full _xSize_. (Note that most of what we're talking about removing has already been removed.   We could focus just on removing parts of the left and right sides of the box.  But that would take two _put_ calls and double the calculations that we need to do.  Therefore it's simplest to approach it the same way we did the previous step.)

So at this point we know the code we need looks like the following:
```
put (xSize,ySize-2,zSize-2) EMPTY (?, ?, ?)
```
We need to figure out the reference point (location) of this EMPTY block. As is shown in the figure above, the reference point is one back and one up from the red block while the _x_ coordinate is the same as that of the red block.  Adding this to our _put_ call and inserting it into the function gives us this:
```
fun wireFrameBox (xSize,ySize,zSize,x,y,z,color) = 
(
    put (xSize,ySize,zSize) color (x,y,z);
    put (xSize-2,ySize-2,zSize  ) EMPTY (x+1,y+1,z  )
    put (xSize  ,ySize-2,zSize-2) EMPTY (x,  y+1,z+1)
);
```
The function call
```
wireFrameBox (14, 5, 10, 0, 0, 0, BLUE);
```
produces the following artifact.

{% include image.html img="functions/wireFrameBox05.png"  alt="Emptied left to right"  %}

#### Step 4: empty box from bottom to top 

The analysis for this step is the same as the previous two. The figure below illustrates the size and location of the EMPTY block that should be placed to clear the top and bottom of the box.
{% include image.html img="functions/wireFrameBox10.jpg"  alt="Empty vertically"  %}

The following completed wireFrameBox function is as follows. 
{% include dotbl.html blfile="functions/wireFrameBox04.bl"  %}
```
fun wireFrameBox (xSize,ySize,zSize,x,y,z,color) = 
(
    put (xSize,ySize,zSize) color (x,y,z);
    put (xSize-2,ySize-2,zSize  ) EMPTY (x+1,y+1,z  );
    put (xSize  ,ySize-2,zSize-2) EMPTY (x,  y+1,z+1);
    put (xSize-2,ySize  ,zSize-2) EMPTY (x+1,y,  z+1)
);
```
The function call
```
wireFrameBox (14, 5, 10, 0, 0, 0, BLUE);
```
produces the following artifact.

{% include image.html img="functions/wireFrameBox06.png"  alt="Wire frame box"  %}

### Patterns and symmetry in the _put_ calls 

Spend a few minutes studying the final version of the function.  Pay particular attention to the patterns that you see in both the size and the locations of the EMPTY blocks.  For example, each horizontal _size_ parameter is either _xSize_ or _xSize-2_ (same for the other two _size_ parameters).  Each horizontal location coordinate is either _x_ or _x+1_ (and same for the other two location parameters).  Many times you can eliminate a little of the work in writing a function like this simply by taking note of such patterns.