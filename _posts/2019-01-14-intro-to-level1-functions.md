---
layout: post
title: Bricklayer Level 1 functions (Vitruvia Concept 5)
categories: [Getting Started]
tags: featured
author: Betty Love
---

<!-- #### Topics on this page
{:.no_toc}
* TOC
{:toc} -->


[My post about Vitruvia Concept 4](/placing-multiple-bricks) discussed how to place the following sequnce of bricks.

1. Put a 1x1 GREEN brick at location (4,3).
2. Put a 2x1 BLUE brick at location (1,0).
3. Put a 4x2 YELLOW brick at location (0,3).
4. Put a 1x2 RED brick at location (3,1).

In this post, we'll consider how to distill these commands to their essentials and have our first look at functions in bricklayer.

What if I rewrote the four statements like the following.  Do you still understand what they say?

1. Put 1x1 GREEN brick at location (4,3).
2. Put 2x1 BLUE brick at location (1,0).
3. Put 4x2 YELLOW brick at location (0,3).
4. Put 1x2 RED brick at location (3,1).

How about now?

1. Put 1x1 GREEN  at location (4,3).
2. Put 2x1 BLUE  at location (1,0).
3. Put 4x2 YELLOW  at location (0,3).
4. Put 1x2 RED  at location (3,1).

And now?

1. Put 1x1 GREEN  at  (4,3).
2. Put 2x1 BLUE  at  (1,0).
3. Put 4x2 YELLOW  at  (0,3).
4. Put 1x2 RED  at  (3,1).

Now?

1. Put 1x1 GREEN  (4,3).
2. Put 2x1 BLUE  (1,0).
3. Put 4x2 YELLOW  (0,3).
4. Put 1x2 RED (3,1).

Once more!

1. put2D_1x1_GREEN(4,3)
2. put2D_2x1_BLUE(1,0)
3. put2D_4x2_YELLOW(0,3)
4. put2D_1x2_RED(3,1)

Ok, the "2D" piece looks a little out of place, but otherwise, can you see the transformation? If so, congratulations!  You're reading and comprehending bricklayer code!

Bricklayer code can place bricks in a two-dimensional (2D) grid like we've been working on in the Vitruvia exercises, but it can also place bricks in a three-dimensional space (typically what one has in mind when building with LEGO).  Dr. Winter reserved the word "put" for programming 3D objects and uses "put2D" to specify two-dimensional objects.
