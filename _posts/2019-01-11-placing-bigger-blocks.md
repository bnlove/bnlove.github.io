---
layout: post
title: Placing blocks that are bigger than 1x1
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
