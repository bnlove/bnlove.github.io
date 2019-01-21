---
layout: post
title: Overwriting--placing blocks on top of blocks (Vitruvia Concept 7)
categories: [Getting Started]
tags: featured
author: Betty Love
---



Thus far our placement of blocks has been analogous to placing physical LEGO blocks on a baseplate. With Vitruvia Concept 7, we diverge from that a bit.  Consider the following bricklayer commands:

> put2D_2x2_RED(0,0)
> put2D_1x1_BLUE(0,0)

If we were building with physical LEGO, then these commands would generate a 2x2 red block with a 1x1 blue block on top of it, as in the following image.

{% include image.html img="vitruvia/concept7-01.png"  alt="blue on top of red blocks" %}

Since we're building with virtual LEGO, when one brick is placed in the same position as another brick, the latter one *overwrites* the first. In this case the commands produced the following artifact.

{% include image.html img="vitruvia/concept7-02.png"  alt="blue overwrites red block" %}

The Bricklayer rule is:

> For a given location, the brick placed there last is the one that is visible.

This feature can frequently be used to our advantage.  Suppose I want to create the following artifact.

{% include image.html img="vitruvia/concept7-03.png"  alt="red and black blocks" %}

Without using Bricklayer's *overwriting* feature, we would need at least seven *put* commands.  One possibility is the following:

> put2D_2x1_RED(0,0)
> put2D_2x1_RED(2,0)
> put2D_1x2_RED(3,1)
> put2D_2x1_RED(2,3)
> put2D_2x1_RED(0,3)
> put2D_1x2_RED(0,1)
> put2D_2x2_BLACK(1,1)

With overwriting, the same thing can be accomplished much more easily, as follows:

> put2D_4x2_RED(0,0)
> put2D_4x2_RED(0,2)
> put2D_2x2_BLACK(1,1)

Clearly the latter way is more clear, easier, and less likely to have errors (as in wrong coordinates).
