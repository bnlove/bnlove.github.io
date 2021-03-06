---
layout: post
title: Functions - Introduction Assuming No Knowledge of Variables
categories: [Variables and Functions]
tags: functions, featured
author: Betty Love
---

#### Topics on this page
{:.no_toc}
* TOC
{:toc}

In this post we'll explore how to create our own functions. This post is similar to the one [here](/functions01) except that one assumes that you're familiar with the _val_ statement.  This one does not. 

So far we've used functions that come with Bricklayer.  These include _put2D_, _put_, _lineXZ_, _circleXZ_, and _sphere_. These are referred to as _built-in_ functions.  We'll learn how to create our own functions which are known as _user-defined_ functions (we are _users_ and _defining_ our own functions).

The primary reason to create your own functions is so that you can use that code multiple times without having to rewrite it each time.  Suppose there was no _circleXZ_ function. To create a circle, you'd have to write a lot of _put_ function calls and it would get complicated quickly. 

***

### Placing the same figure in multiple locations

Suppose we want to write a bricklayer program to create the following figure.
{% include image.html img="functions/functions01.png"  alt="Functions01"  %}

The Level_3 code to create the figure at (0,0) is as follows.
{% include dotbl.html blfile="functions/functions01.bl"  %}
```
put2D  (2,4)  BLUE    (0,0);
put2D  (3,3)  RED     (2,0);
put2D  (2,3)  YELLOW  (0,4);
put2D  (3,4)  GREEN   (2,3);
```

Now let's write the code to place the other figures.  One way to do this is to look at the grid and use the labels on the rows and columns to get the coordinates for each of the blue, red, yellow, and green blocks.  For the figure at (14,0), the blue one is at (14,0), the red at (16,0), yellow at (14,4), and green at (16,3). For the figure at (7,6), the blue one is at (7,6), the red at (9,6), yellow at (7,10), and green at (9,9).  We could do this for each of the figures.  Following is the code to create all six figures.
 {% include dotbl.html blfile="functions/functions02.bl"  %}


```
(* Figure at (0,0) *)
put2D  (2,4)  BLUE    (  0 ,  0 );
put2D  (3,3)  RED     (  2 ,  0 );
put2D  (2,3)  YELLOW  (  0 ,  4 );
put2D  (3,4)  GREEN   (  2 ,  3 );

(* Figure at (14,0) *)
put2D  (2,4)  BLUE    ( 14 ,  0 );
put2D  (3,3)  RED     ( 16 ,  0 );
put2D  (2,3)  YELLOW  ( 14 ,  4 );
put2D  (3,4)  GREEN   ( 16 ,  3 );

(* Figure at (7,6) *)
put2D  (2,4)  BLUE    (  7 ,  6 );
put2D  (3,3)  RED     (  9 ,  6 );
put2D  (2,3)  YELLOW  (  7 , 10 );
put2D  (3,4)  GREEN   (  9 ,  9 );

(* Figure at (4,15) *)
put2D  (2,4)  BLUE    (  4 , 15 );
put2D  (3,3)  RED     (  6 , 15 );
put2D  (2,3)  YELLOW  (  4 , 19 );
put2D  (3,4)  GREEN   (  6 , 18 );

(* Figure at (13,13) *)
put2D  (2,4)  BLUE    ( 13 , 13 );
put2D  (3,3)  RED     ( 15 , 13 );
put2D  (2,3)  YELLOW  ( 13 , 17 );
put2D  (3,4)  GREEN   ( 15 , 16 );

(* Figure at (20,11) *)
put2D  (2,4)  BLUE    ( 20 , 11 );
put2D  (3,3)  RED     ( 22 , 11 );
put2D  (2,3)  YELLOW  ( 20 , 15 );
put2D  (3,4)  GREEN   ( 22 , 14 );
```

That gets tedious fast!  Suppose that instead of six of these figures, you wanted to place 20? Or 100? You'd want an easier way!  The key is to notice that the relative position of the red block to the blue block and the green block to the blue block, etc. does not change.  So if the blue block moves over 4 and up 15, so does the red block and the green block and the yellow block.  So whatever we add to the coordinates of the blue block, we do the same to the coordinates of the other blocks.  Take a look at the following graphic to understand this better.

{% include image.html img="functions/functions02.jpg"  alt="Functions02"  %}

Based on this analysis, we can rewrite our program as follows (yes, it looks even more tedious, but it will be worth it!).
{% include image.html img="functions/functions03.png"  alt="Functions03"  %}

Now that we can see the patterns in the code, we can create a function that does the work for us.  The following function places a copy of the figure at location (x,z).
 {% include dotbl.html blfile="functions/functions03.bl"  %}

```
open Level_3;

fun myfigure ( x, z ) =
(
    put2D  (2,4)  BLUE    (  x + 0,  z + 0 );
    put2D  (3,3)  RED     (  x + 2,  z + 0 );
    put2D  (2,3)  YELLOW  (  x + 0,  z + 4 );
    put2D  (3,4)  GREEN   (  x + 2,  z + 3 )
);
 
build2D (30,30);

myfigure ( 0,  0);      (* figure at ( 0,  0) *)
myfigure (14,  0);      (* figure at (14,  0) *)
myfigure ( 7,  6);      (* figure at ( 7,  6) *)
myfigure ( 4, 15);      (* figure at ( 4, 15) *)
myfigure (13, 13);      (* figure at (13, 13) *)
myfigure (20, 11);      (* figure at (20, 11) *)

show2D "my blocks"
```