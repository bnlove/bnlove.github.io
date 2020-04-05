---
layout: post
title: The mod function 
categories: [Functions]
tags: functions, level5
author: Betty Love
---

#### Topics on this page
{:.notoc}
* TOC
{:toc}

***

In this post we'll investigate the _mod_ function.

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

