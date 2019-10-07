---
layout: post
title: Creating an arbitrary element of a visual sequence
categories: [Functions]
tags: functions
author: Betty Love
---

#### Topics on this page
{:.notoc}
* TOC
{:toc}

***

In this post we'll write code to creating an arbitrary element of the visual sequence below.  
{% include image.html img="val/sequence01.png"  alt="sequence01"  %}

First we need to understand the sequence in terms of size and location of key parts.  It is clear that there are two parts: the blue part and the red part. We'll analyze each.  First, the blue block.  We'll assume that the lower left corner of the element that we're analyzing is (xLL,zLL) (for lower-left x coordinate and lower-left z coordinate).

| &nbsp; Element # &nbsp;| &nbsp; Width &nbsp; | &nbsp; Height &nbsp; | &nbsp; LL x&nbsp;  | &nbsp; LL z &nbsp; |
|:---:     |:---:   |:---:   |:---: |:---:|
|1         | 2     | 1      | xLL  | zLL|
|2         | 2     | 2      | xLL  | zLL |   
|3         | 2     | 3      | xLL  | zLL  | 
|4         | 2     | 4      | xLL  | zLL  |
|---       | ---   | ---    | ---  | ---|
|n         | 2     | n      | xLL  | zLL | 

So the code to create the blue block for element _n_ at _(xLL,zLL)_ will be
```
put2D (2,n) BLUE (xLL,zLL);
```

Now for the red block:

| &nbsp; Element # &nbsp;| &nbsp; Width &nbsp; | &nbsp; Height &nbsp; | &nbsp; LL x&nbsp;  | &nbsp; LL z &nbsp; |
|:---:     |:---:   |:---:   |:---: |:---:|
|1         | 1     | 1      | xLL+2  | zLL|
|2         | 1     | 1      | xLL+2  | zLL |   
|3         | 1     | 1      | xLL+2  | zLL  | 
|4         | 1     | 1      | xLL+2  | zLL  |
|---       | ---   | ---    | ---  | ---|
|n         | 1     | 1      | xLL+2  | zLL | 

The code to create the red block for element _n_ at _(xLL,zLL)_ will be
```
put2D (1,1) RED (xLL+2,zLL);
````

Let's write the code to create the figure above with elements 1 through 4.




It will be based on parameters to define the following:

    - location
    - size 
    - colors
    
### Step 1 - code to create one artifact at (0,0)

To make this step easier, let's start with the prototype created in the bricklayer.org Grid app:
{% include image.html img="functions/crissCrossSquare02.png"  alt="Criss-cross square on grid"  %}

The following code will create this artifact.
{% include dotbl.html blfile="functions/crissCrossSquare01.bl"  %}
```
put2D (10,10) BLUE (0,0);
lineXZ (0,0) (9,9) YELLOW;
lineXZ (0,9) (9,0) YELLOW;
```

### Step 2 - code to create one artifact at an arbitrary location

Let's start by writing the code to create the artifact at (6,3).  The animation below illustrates how the coordinates of the artifact change as it moves from (0,0) to (6,3).  
{% include image.html img="functions/crissCrossSquare04.gif"  alt="Criss-cross square animation"  %}

Consider what is happening to the _x-coordinates_ of each of the blocks in the artifact as it is moved.  For example, the lower-left corner of the square starts at (0,0) and moves to the right until it gets to (6,0).  Along the way, it passed through (1,0), (2,0), (3,0), etc.  And what happens to the _z-coordinates_?  They all stay the same until the artifact starts to move upward.  The lower-left corner goes from (6,0) to (6,1), (6,2), and then to (6,3).

Let's look at a different block, say, the upper right one that starts at (9,9). As the artifact moves the right, this block goes to (10,9), (11,9), (12,9), etc until it gets to (15,9).  Then it starts to move upward and goes to (15,10), (15,11), and finally (15,12).  

By moving the artifact from (0,0), to (6,3), we are _translating_ each block to the right by 6 and up by 3.  This means that if the coordinates of a block in the initial artifact were _(a,b)_, in the new position, that block will be at _(a+6,b+3)_.  Some examples: 

    - (0,0) moved to (0+6,0+3) = (6,3)
    - (9,9) moved to (9_6,9+3) = (15,12)
    - (2,5) moved to (2+6,5+3) = (8,8)

If I want to move the artifact to an arbitrary location, say, (xLoc,zLoc), I need to add _xLoc_ to the first coordinate of each block and _zLoc_ to the second coordinate of each block.  Examples:

    - (0,0) moves to (0+xLoc,0+zLoc)
    - (9,9) moves to (9+xLoc,9+zLoc)
    - (2,5) moves to (2+xLoc,5+zLoc)
    
Therefore my function to place a copy of the artifact at (xLoc,zLoc) would be as follows.
{% include dotbl.html blfile="functions/crissCrossSquare02.bl"  %}
```
fun crissCrossSquare (xLoc,zLoc) = 
(
    put2D (10,10) BLUE (0+xLoc,0+zLoc);
    lineXZ (0+xLoc,0+zLoc) (9+xLoc,9+zLoc) YELLOW;
    lineXZ (0+xLoc,9+zLoc) (9+xLoc,0+zLoc) YELLOW
);
```
To place a copy at (6,3), use the function call:
```
crissCrossSquare (6,3);
```
The output is as follows (red brick placed at (0,0) for reference)
{% include image.html img="functions/crissCrossSquare07.png"  alt="Criss-cross square at (6,3)"  %}


### Step 3 - add parameters for colors

Now suppose we'd like to create the criss-cross square artifact in different colors.  We need to specify a color for the square and a color for the lines.  Let's call the color for the square _squareColor_ and the color for the lines _lineColor_.  We'll add these parameters to our function and substitute _squareColor_ for BLUE and _lineColor_ for YELLOW.  Now our function is as follows.
{% include dotbl.html blfile="functions/crissCrossSquare03.bl"  %}
```
fun crissCrossSquare (xLoc,zLoc,squareColor,lineColor) = 
(
    put2D (10,10) squareColor (0+xLoc,0+zLoc);
    lineXZ (0+xLoc,0+zLoc) (9+xLoc,9+zLoc) lineColor;
    lineXZ (0+xLoc,9+zLoc) (9+xLoc,0+zLoc) lineColor
);
```
The following code places a blue and yellow copy at (0,0) and a pink and violet copy at (13,5)
```
crissCrossSquare (0,0,BLUE,YELLOW);
crissCrossSquare (13,5,PINK,VIOLET);
```
{% include image.html img="functions/crissCrossSquare09.png"  alt="Criss-cross squares"  %}


### Step 4 - add parameters for size

Now consider how we could modify our function so that we can create a copy of the artifact of an arbitrary size.  First let's think about what that means.  Let's go back to the initial code to create a criss-cross square at (0,0) and examine which parts of it relate to size. In the figure below, we see that clearly the size of the square depends on the size of the artifact.  Does anything else?
{% include image.html img="functions/crissCrossSquare11.jpg"  alt="Criss-cross square code"  %}

Yes!  The endpoints of the two lines are the corners of the square, so they will depend on the size of the square.
For a square of size 10 placed at (0,0), the endpoints of the two lines are:

      - (0,0) and (9,9)
      - (0,9) and (9,0)

How can we represent (9,9), (0,9) and (9,0) in terms of the size of the square (10 in this case)? How about the following:

      - (0,0) and (10-1,10-1)
      - (0,10-1) and (10-1,0)
      
So in general, for a square of size _squareSize_ placed at (0,0), the endpoints of the two lines would be:

      - (0,0)            and (squareSize-1,squareSize-1)
      - (0,squareSize-1) and (squareSize-1,0)

Now we just need to _translate_ those coordinates to (_xLoc_,_zLoc_) as we did in Step 2 above.

      - (  0         ,   0        ) moves to (     0       + xLoc,      0       + zLoc)
      - (squareSize-1,squareSize-1) moves to (squareSize-1 + xLoc, squareSize-1 + zLoc)
      - (  0         ,squareSize-1) moves to (     0       + xLoc, squareSize-1 + zLoc)
      - (squareSize-1,   0        ) moves to (squareSize-1 + xLoc,      0       + zLoc)

Incorporating this into our function with a new parameter _squareSize_ yields the following.
{% include dotbl.html blfile="functions/crissCrossSquare03.bl"  %}
```
fun crissCrossSquare (xLoc,zLoc,squareColor,lineColor,squareSize) = 
(
    put2D (squareSize,squareSize) squareColor (0+xLoc,0+zLoc);
    lineXZ ( 0 + xLoc,      0       + zLoc) (squareSize-1 + xLoc, squareSize-1 + zLoc) lineColor;
    lineXZ ( 0 + xLoc, squareSize-1 + zLoc) (squareSize-1 + xLoc,      0       + zLoc) lineColor
);
```

The following code places a blue and yellow copy of size 10 at (0,0), a pink and violet copy of size 15 at (13,5), and a red and white copy of size 7 at (2,12).
```
crissCrossSquare ( 0,  0, BLUE, YELLOW, 10);
crissCrossSquare (13,  5, PINK, VIOLET, 15);
crissCrossSquare ( 2, 12, RED , WHITE ,  7);
```
{% include image.html img="functions/crissCrossSquare13.png"  alt="Criss-cross squares"  %}


  


  
      




