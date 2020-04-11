---
layout: post
title: Variables - Using Numeric Variables to Represent Coordinates
categories: [Variable and Functions]
tags: variables, featured
author: Betty Love
---

#### Topics on this page
{:.no_toc}
* TOC
{:toc}

In the last [post](/variables-numbers01) we explored using variables to represent numbers, specifically coordinates defining the location that we wanted to place a figure.  The figure we used was fairly simple and so perhaps did not convince you that all this extra work was worthwhile.  So in this post, we'll look at a slightly more complicated figure.  

***

### Placing the same figure in multiple locations

Suppose we want to write a bricklayer program to create the following figure.
{% include image.html img="val/functions01.png"  alt="Functions01"  %}

We could take the brute-force approach and ignore the fact that we're creating the same figure in six different places.  But that is a beginner's approach and we're not beginners at this point.  Also, suppose you wanted to place the figure in ten places, or 20 or 100?  You certainly wouldn't want to use the brute-force approach then.  So let's use our brains.

### Code for just one figure

Let's start by looking at just one of the figures and write the code to place it at an arbitrary location.  
We need variables to represent that location, which is the lower-left corner of the figure.  We will use _(xLoc, zLoc)_ for this.  So that means the blue block will be placed at _(xLoc, zLoc)_.  The values for _xLoc_ and _zLoc_ will need to be specified in _val_ statements.  But our code should work for any valid values for these variables.


Given that the lower left blue block is at _(xLoc, zLoc)_, where is the lower left red block?  Notice in the image below that the lower-left red block has the same _z_ coordinate as the blue block.  What about the _x_ coordinate?  As shown below, it's two places to the right of the lower-left blue block, so would be at _xLoc + 2_.  Therefore the location of the red block is _(xLoc + 2, zLoc)_
{% include image.html img="val/val-num04.png"  alt="val-num04"  %}

Take a look at the image below and see if you an figure out the coordinates of the yellow and green blocks.
 {% include image.html img="val/val-num06.png"  alt="val-num06"  %}

The yellow block has the same _x_ coordinate as the blue block, but is four spaces up, so we need to add 4 to _zLoc_.  This gives us _(xLoc, zLoc + 4)_.  For the green block we go over two spaces and up three, so it's location is _(xLoc + 2, zLoc + 3)_.

The code will look like the following (before running, we'll need to plug in numbers where the question marks are!):
```
val xLoc = ?;  (* lower-left x coordinate of figure *)
val zLoc = ?;  (* lower-left z coordinate of figure *)

put2D  (2,4)  BLUE    ( xLoc     , zLoc     );
put2D  (3,3)  RED     ( xLoc + 2 , zLoc     );
put2D  (2,3)  YELLOW  ( xLoc     , zLoc + 4 );
put2D  (3,4)  GREEN   ( xLoc + 2 , zLoc + 3 );
```

The important thing to note is that we can now place the figure anywhere we want just by changing the _val_ statements.  No changes to the _put2D_ statements are required at all!

### Create the original figure

Now let's write the code to create the original image which consists of six copies of our figure.  Scroll up a bit and note that the the copies appear at the following coordinates (0,0), (14,0), (7,5), (4,15), (13,13), and (20,11). We just make a copy of the code above for each figure and for each, set _xLoc_ and _zLoc_ in the _val_ statements.  The result is shown in the figure below.  Note that the green sections of code are all identical; only the yellow sections with the _val_ statements changes. This distinction is critical since we'll soon learn that we only need to include the green section of code once in our programs (in our own function).
{% include dotbl.html blfile="val/val-num03.bl"  %}
{% include image.html img="val/val-num07.png"  alt="val-num07"  %}

The graphic below shows the equivalent segments of code.
{% include image.html img="val/val-diagram.png"  alt="val-diagram"  %}