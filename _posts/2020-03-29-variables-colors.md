---
layout: post
title: Getting Started with Variables to Represent Colors
categories: [Getting Started, Functions]
tags: functions
author: Betty Love
---

#### Topics on this page
{:.no_toc}
* TOC
{:toc}

In this post we'll explore how to use variables. Variables are handy when you'd like to use the same code, but with different values (numbers or colors).

***

### Creating the same figure with different sets of colors

Suppose we want to create the following figure.
{% include image.html img="val/love01.png"  alt="love-numbers"  %}

The Level_3 code to create the figure at (0,0) is as follows.
{% include dotbl.html blfile="val/love01.bl"  %}
```
(* Outline *)
put2D (17, 19)  RED    ( 0,  0);

(* Four panes background *)
put2D ( 7,  8)  WHITE  ( 1,  1);
put2D ( 7,  8)  WHITE  ( 9,  1);
put2D ( 7,  8)  WHITE  ( 1, 10);
put2D ( 7,  8)  WHITE  ( 9, 10);

(* L *)
put2D ( 5,  1)  BLACK  ( 2, 11);
put2D ( 1,  6)  BLACK  ( 2, 11);

(* O *)
put2D ( 3,  1)  BLACK  (11, 11);
put2D ( 3,  1)  BLACK  (11, 16);
put2D ( 1,  4)  BLACK  (10, 12);
put2D ( 1,  4)  BLACK  (14, 12);

(* V *)
put2D ( 1,  3)  BLACK  ( 2,  5);
put2D ( 1,  3)  BLACK  ( 3,  3);
put2D ( 1,  2)  BLACK  ( 4,  2);
put2D ( 1,  3)  BLACK  ( 5,  3);
put2D ( 1,  3)  BLACK  ( 6,  5);

(* E *)
put2D ( 5,  1)  BLACK  (10,  2);
put2D ( 5,  1)  BLACK  (10,  7);
put2D ( 3,  1)  BLACK  (10,  5);
put2D ( 1,  6)  BLACK  (10,  2);
```

Suppose we'd like to create the same figure, but using different colors. For example, instead of red, white, and black, we want blue, green, and yellow.  One approach is to manually change every occurrence of RED to BLUE, every occurrence of WHITE to GREEN, and every occurrence of BLACK to YELLOW.  We could even be smart and use the Find/Replace option in the editor.  We'd have the following code.

```
(* Outline *)
put2D (17, 19)  BLUE    ( 0,  0);

(* Four panes background *)
put2D ( 7,  8)  GREEN  ( 1,  1);
put2D ( 7,  8)  GREEN  ( 9,  1);
put2D ( 7,  8)  GREEN  ( 1, 10);
put2D ( 7,  8)  GREEN  ( 9, 10);

(* L *)
put2D ( 5,  1)  YELLOW  ( 2, 11);
put2D ( 1,  6)  YELLOW  ( 2, 11);

(* O *)
put2D ( 3,  1)  YELLOW  (11, 11);
put2D ( 3,  1)  YELLOW  (11, 16);
put2D ( 1,  4)  YELLOW  (10, 12);
put2D ( 1,  4)  YELLOW  (14, 12);

(* V *)
put2D ( 1,  3)  YELLOW  ( 2,  5);
put2D ( 1,  3)  YELLOW  ( 3,  3);
put2D ( 1,  2)  YELLOW  ( 4,  2);
put2D ( 1,  3)  YELLOW  ( 5,  3);
put2D ( 1,  3)  YELLOW  ( 6,  5);

(* E *)
put2D ( 5,  1)  YELLOW  (10,  2);
put2D ( 5,  1)  YELLOW  (10,  7);
put2D ( 3,  1)  YELLOW  (10,  5);
put2D ( 1,  6)  YELLOW  (10,  2);
```

That code produces the following figure. 
{% include dotbl.html blfile="val/love02.bl"  %}
{% include image.html img="val/love02.png"  alt="love02"  %}

And if we wanted another set of colors, we could do all those changes again. But there's another way.  And although it may not seem to be a big deal for this example, you'll find out soon that it is a major time saver for future projects.

The key is using variables.  A variable can take on different values. In our example, we need a color for the outer frame, another for the four panes, and another for the letters.  So let's create three variables; we can name them whatever we'd like, but it's best to give them descriptive names, like _frameColor_, _paneColor_, and _letterColor_, rather than _a_, _b_, and _c_.  

I'm going to rewrite the original code and everywhere I have RED, I'm going to put frameColor; everywhere I have WHITE, I'm going to put paneColor, and everywhere I have BLACK, I'm going to put letterColor.  Here's what that looks like.

```
(* Outline *)
put2D (17, 19)  frameColor    ( 0,  0);

(* Four panes background *)
put2D ( 7,  8)  paneColor  ( 1,  1);
put2D ( 7,  8)  paneColor  ( 9,  1);
put2D ( 7,  8)  paneColor  ( 1, 10);
put2D ( 7,  8)  paneColor  ( 9, 10);

(* L *)
put2D ( 5,  1)  letterColor  ( 2, 11);
put2D ( 1,  6)  letterColor  ( 2, 11);

(* O *)
put2D ( 3,  1)  letterColor  (11, 11);
put2D ( 3,  1)  letterColor  (11, 16);
put2D ( 1,  4)  letterColor  (10, 12);
put2D ( 1,  4)  letterColor  (14, 12);

(* V *)
put2D ( 1,  3)  letterColor  ( 2,  5);
put2D ( 1,  3)  letterColor  ( 3,  3);
put2D ( 1,  2)  letterColor  ( 4,  2);
put2D ( 1,  3)  letterColor  ( 5,  3);
put2D ( 1,  3)  letterColor  ( 6,  5);

(* E *)
put2D ( 5,  1)  letterColor  (10,  2);
put2D ( 5,  1)  letterColor  (10,  7);
put2D ( 3,  1)  letterColor  (10,  5);
put2D ( 1,  6)  letterColor  (10,  2);
```

Now this code won't run because we haven't defined what the values of our variables are.  To do that, we use and new kind of bricklayer statement: the _val_ statement. It's pretty straightforward. We just set each of our variables equal to the value we want it to have.  In our example, the code looks like this.

```
val frameColor  = RED;
val paneColor   = WHITE;
val letterColor = BLACK;
```

Makes sense, right?  Ok, make sure that you put these three statements at the beginning of your code (after the build2D statement) since you have to define the values of the variables before the variables appear in the code.  Whole program: 
{% include dotbl.html blfile="val/love03.bl"  %}

The output is the same as the original code:
{% include image.html img="val/love03.png"  alt="love03"  %}

How do we change the colors?  Just change them in the _val_ statements.  If we want blue, green, and yellow, the _val_ statements would look like this.

```
val frameColor  = BLUE;
val paneColor   = GREEN;
val letterColor = YELLOW;
```

NONE OF THE OTHER CODE NEEDS TO CHANGE!!

Try it out!  Put in your own combination of colors and see what happens!  Explore!!