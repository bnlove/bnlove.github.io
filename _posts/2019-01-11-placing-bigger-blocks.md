---
layout: post
title: Placing blocks that are bigger than 1x1 (Vitruvia Concept 3)
categories: [Getting Started]
tags: featured
author: Betty Love
---

<!-- #### Topics on this page
{:.no_toc}
* TOC
{:toc} -->


In Vitruvia Concept 1, you are asked to place 1x1 bricks at various locations.  When you get to Concept 3, however, things may seem a little confusing since you are asked to place larger bricks.  For example, Concept 3 Exercise 7 is as follows:

> Put a 4x2 YELLOW brick at location (0,3).

Location (0,3) is just one cell, right?  Just one position in the grid.  So how does one put a 4x2 brick there? The answer is that the location given is where the *bottom left corner* of the brick goes. This is the way Dr. Winter designed and implemented bricklayer.

So...to put a 4x2 YELLOW brick at location (0,3), we must first find location (0,3). Remember *over and up* or Dr. Winter's *run before you jump* to locate (0,3).

Actually, we should first click on YELLOW so that when we find location (0,3), we can click on it and put a YELLOW block there.

{% include image.html img="vitruvia/concept3-01.jpg"  alt="Vitruvia Concept 3 Exercise 7" %}

Now we need to figure out what a 4x2 brick looks like.  Basically the question is: is it 4 wide and 2 tall or 4 tall and 2 wide???  The answer is that it follows the same convention as the grid coordinates.  The first number is how far *over* (*wide*) and the second is how far *up* (*tall*) as shown in the following figure.

{% include image.html img="vitruvia/concept3-02.jpg"  alt="4x2 vs 2x4 brick" %}

We go back to our Vitruvia grid and click in positions (1,3), (2,3), (3,3), (4,3), (0,4), (1,4), (2,4), (3,4) to complete the 4x2 brick at location (0,3).


{% include image.html img="vitruvia/concept3-03.png"  alt="Vitruvia Concept 3 Exercise 7 solution" %}

***

### Another example

Suppose we are asked to place a 2x3 RED block at (1,0).  Following are the steps to go through to accomplish this.

1. Click on the RED brick to select RED as the color.
{% include image.html img="vitruvia/select-red.png"  alt="Vitruvia select red as color" %}

{:start="2"}
2. Click on location (1,0).  Recall that this will be the *lower left corner of the brick we're placing*. Also remember *over and up*, so go over 1 and up 0 to get to location (1,0).
{% include image.html img="vitruvia/whereis1-0.jpg"  alt="Where is (1,0)" %}

{:start="3"}
3. We are to place a 2x3 block.  Again remembering *over and up*, this block will be 2 *over* (*wide*) and 3 *up* (*tall*).  
{% include image.html img="vitruvia/2-3or3-2.jpg"  alt="2x3 or 3x2" %}
Using the brick we've already placed in location (1,0) as the lower left corner, we click on cells (2,0), (1,1), (2,1), (1,2), and (2,2) to complete the 2x3 red brick.

{% include image.html img="vitruvia/2x3red-at1-0.png"  alt="2x3 red at (1,0)" %}
