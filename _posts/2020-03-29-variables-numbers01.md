---
layout: post
title: Getting Started with Variables to Represent Numbers
categories: [Getting Started, Functions]
tags: functions
author: Betty Love
---

#### Topics on this page
{:.no_toc}
* TOC
{:toc}

In this post we'll explore how to use variables to represent numbers. Variables are handy when you'd like to use the same code, but with different values.  If you haven't read about using variables to represent colors, I recommend you do that before proceeding.  You can find it [here](/variables-colors).

***

### Placing the same figure in multiple locations

Suppose we want to write a bricklayer program to create the following figure (just the blue and yellow part).
{% include image.html img="val/val-num01.png"  alt="val-num01"  %}

Your might wonder where to put it.  I didn't say.  What I'd like is to have code that would work for any location that I specify. Think back to the post referenced above in which we wrote code to create a particular figure and specified the colors to use in _val_ statements.  To switch to different colors, we only needed to change the values defined in the _val_ statements. 

That's the idea for what we want to do here.  Let's use _val_ statements to define the location (lower-left corner) of the figure and write the code using the variables defined in the _val_ statements. Here's a visual of this idea.
{% include image.html img="val/val-num02.png"  alt="val-num02"  %}

So let's assume that we start with the following (question marks to be replaced with numbers when we decide where we want the figure to go):
```
val xLoc = ?;  (* lower-left x coordinate of figure *)
val zLoc = ?;  (* lower-left z coordinate of figure *)
```

We can start by writing the code to place a 6x4 blue block (then we'll overwrite it to put the yellow part in).  Since _xLoc_ and _zLoc_ will already have been defined (assigned values) when we get to this part of our program, we can use them just like we would any numbers.

If we weren't using variables and we wanted to put the blue block at (5,8), the code would be:
```
put2D (6,4) BLUE (5,8);
```

So we write the same code, except substitute _(xLoc, zLoc)_ for the location, as follows:
```
put2D (6,4) BLUE (xLoc, zLoc);
```

When you run your program, the computer automatically plugs in whatever values you've specified for _xLoc_ and _zLoc_.

Ok, we still need to place the yellow block.  This is a little trickier because we have to base its position on the location of the blue block.  Now, if you had placed the blue block at (5,8), the yellow block would go.....where?  One space to the right in the _x_ direction and one up in the _z_ direction.  So (5+1,8+1)  (which we'd just write as (6,9)). 

But if the blue block is at _(xLoc, zLoc)_, then where does the yellow block go?  The same logic applies: one space to the right and one space up.  So how do we write that? Same way I did in the previous paragraph, namely, _(xLoc + 1, zLoc + 1)_! That's it!
Here's the code to create the whole figure:
```
put2D (6,4) BLUE   (xLoc    , zLoc    );
put2D (4,2) YELLOW (xLoc + 1, zLoc + 1);
```

The complete program to make the figure at (5,8) is as follows:
{% include dotbl.html blfile="val/val-num01.bl"  %}
```
open Level_3;

build2D (20,20);

val xLoc = 5;  (* lower-left x coordinate of figure *)
val zLoc = 8;  (* lower-left z coordinate of figure *)

put2D (6,4) BLUE   (xLoc    , zLoc    );  (* place blue block *)
put2D (4,2) YELLOW (xLoc + 1, zLoc + 1);  (* place yellow block *)

show ""
```

### Why would we do this?

At this point some of you may be thinking that this seems to be a lot of trouble for nothing.  In particular, the program above could be written much more easily as follows.
```
put2D (6,4) BLUE   (5,8);  (* place blue block *)
put2D (4,2) YELLOW (6,9);  (* place yellow block *)
```

Much more straightforward, right?  Half the lines of code!  So what is the point?

Good question!  The primary answer is that being able to write the code using variables allows us to reuse the main part of the program (the put statements) without changing them at all.  To put the figure in a different place, we only need to change the val statements.  We've done the hard work (figuring out the locations of the blocks) and we don't need to ever do that again, no matter where we want to place that figure.  Soon we'll learn about writing our own functions and will see how this can really streamline our programs.  We're not quite ready for that yet though.

### How do a I change variable values?

Suppose we wanted to put our figure in multiple locations, say, at (5,8), (2,12), (8,1), and (0,3).  Since we've done the hard part (figured out the code to create the figure anywhere we want), all we need to do is change the values defined for _xLoc_ and _zLoc_ in the val statements, once for each location.  The code for this is below.  Note that the only part of the program that changes is the _val_ statements.  The _put2D_ statements are all the same.
{% include dotbl.html blfile="val/val-num02.bl"  %}
{% include image.html img="val/val-num03.png"  alt="val-num03"  %}

### Still seems like a lot of work...

For this simple program, it may not be a big deal to do the arithmetic to place the figure at different locations.  So how about a more complicated program? Continue  [here] (/variables-numbers02).