---
layout: post
title: Counting items in a list
categories: [Getting Started]
tags:  counting
author: Betty Love
---

<!-- #### Topics on this page
{:.no_toc}
* TOC
{:toc} -->

We all know how to count, right?  Seems obvious.  Sometimes, however, it's not so obvious. Suppose there are 20 people in our class and each is assigned a number between 1 and 20.  I then say I want people with numbers 5 through 12 to stand up.  How many people will stand up?

Many people automatically subtract 5 from 12 and say 7.  But is this correct?  (Probably not or I wouldn't be going on about this!) The best way to figure this out is to actually count the people with numbers 5 through 12, or equivalently, to count the numbers 5 through 12.  See the figure below for this.

{% include image.html img="counting/counting-list01.png"  alt="Counting elements of a list" %}

As you see, there are *8* people with number between 5 and 12.  So one more than the 7 that many people assumed at first.  This is a very common error!

Let's try another one. Take a look at the figure below. I have blue blocks in positions3 through 15.  How many blue blocks are there?
{% include image.html img="counting/blue-blocks.png"  alt="Counting blue blocks" %}

Again, your first try might be to subtract 3 from 15 and say 12.  But maybe you're thinking that that strategy didn't work well in our first example.  So maybe we should count.
{% include image.html img="counting/blue-blocks02-600.png"  alt="Counting blue blocks again" %}

So we get 13 instead of 12.  Hmm...I'm starting to see a pattern here.  If we just subtract the smaller number from the larger, we're one off every time.  Actually we're one short.  So maybe we should still do the subtraction, but then add one.  If we took this approach,  we would count the people with numbers 5 through 12 as follows:

12 - 5 + 1 = 8


And we'd count the blue blocks like this:

15 - 3 + 1 = 13


So if we wanted to come up with a formula for counting the number of items in a list between a starting point (I'll call *start*) and a stopping point (I'll call *stop*), it would be the following:

*stop - start + 1*
