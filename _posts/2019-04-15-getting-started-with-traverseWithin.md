---
layout: post
title: The traverseWithin function
categories: [Functions]
tags: functions, level5
author: Betty Love
---

#### Topics on this page
{:.notoc}
* TOC
{:toc}

***

In this post we'll investigate the _traverseWithin_ function from Level_5.  

### Example 1

Let's start with a small example.  Consider the program below.
{% include dotbl.html blfile="level5/traverseWithin01.bl"  %}
```
open Level_5;

fun xLessThan2 (x, y, z) =
    if x < 2 then GREEN else YELLOW;

build (5,1,5);

traverseWithin (0,0,0)  (4,0,4)  xLessThan2;

show ""
```
The output is as follows.
{% include image.html img="level5/traverseWithin01a.png"  alt="Artifact "  %}

So...how does this work?

The _traverseWithin_ function is a very powerful function, unlike any we've seen before.  Let's look at its parameters.  The general form is:
> traverseWithin   startLocation    endLocation    someFunction;

The function _someFunction_ will be applied to every location between (and including) _startLocation_ and _endLocation_.

In our example, the _startLocation_ is (0,0,0) and the _endLocation_ is (4,0,4).  Let's start by figuring out which locations are defined by these parameters.  We'll look at each coordinate:

      * x goes 0 to 4: 0,1,2,3,4
      * y goes 0 to 0: 0
      * z goes 0 to 4: 0,1,2,3,4

We can list all the locations as follows:
{% include image.html img="level5/traverseWithin03.png"  alt="traverseWithin space"  %}

Another way to think about the set of locations is graphically.  We want all locations where _x_ is between 0 and 4, _y_ is 0, and _z_ is between 0 and 4.  Here is that space in the _x-z_ plane.

{% include image.html img="level5/traverseWithin02.jpg"  alt="traverseWithin space"  %}


So now that we know what space we're working with, let's turn our attention to the third parameter of the _traverseWithin_ function which is the name of another function.  In our example, this function is _xLessThan2_. The function call:
```
traverseWithin (0,0,0)  (4,0,4)  xLessThan2;
```

tells the computer to apply _xLessThan2_ to each location defined by the starting point (0,0,0) and the ending point (4,0,4).  We can go down our list of locations and see what the results are.
{% include image.html img="level5/traverseWithin04.png"  alt="traverseWithin space"  %}

We can also look at this graphically.  The condition _x<2_ is evaluated for each cell in the grid.
{% include image.html img="level5/traverseWithin05.png"  alt="traverseWithin space"  %}

### Example 2

Let's look at another example using the same starting and ending locations, but with a different function.  Specifically, take a look at the code below.
{% include dotbl.html blfile="level5/traverseWithin02.bl"  %}
```
open Level_5;

fun aLine (x, y, z) =
    if x = z then RED else BLACK;

build (5,1,5);

traverseWithin (0,0,0)  (4,0,4)  aLine;

show ""
```

Since the set of locations that we're traversing is the same as before, we can focus on the  function that will be applied to the coordinates of each location, _aLine_. The function call:
```
traverseWithin (0,0,0)  (4,0,4)  aLine;
```

tells the computer to apply _aLine_ to each location defined by the starting point (0,0,0) and the ending point (4,0,4).  We can go down our list of locations and see what the results are.
{% include image.html img="level5/traverseWithin07.png"  alt="traverseWithin space"  %}

Again, we can also look at this graphically.  The condition _x=z_ is evaluated for each cell in the grid.
{% include image.html img="level5/traverseWithin08.png"  alt="traverseWithin space"  %}

### One more example---make our own circle function!

Just to get a little crazy, let's try to make our own circle function using _traverseWithin_.  First, we have to know how to describe a circle mathematically.  See the figure below which includes information from [WolframAlpha](https://www.wolframalpha.com/input/?i=circle) and my annotations.  
{% include image.html img="level5/traverseWithin09.jpg"  alt="circle specifications"  %}

Our circle function will be very basic.  It will create a blue circle of radius 10 with center (12,15).  The part of the region outside circle will be yellow. 
{% include dotbl.html blfile="level5/traverseWithin03.bl"  %}
```
open Level_5;

fun myBasicCircle (x, y, z) =
    if ((x-12)*(x-12) + (z-15)*(z-15) <= 10*10) then BLUE else YELLOW;

build (30,1,30);

traverseWithin (0,0,0)  (29,0,29)  myBasicCircle;

show ""
```

The following figure shows the locations processed by the _traverseWithin_ function and the corresponding values. 
{% include image.html img="level5/traverseWithin10.png"  alt="circle specifications"  %}

Output from running the code is shown in the following figure.
{% include image.html img="level5/traverseWithin11.png"  alt="circle specifications"  %}