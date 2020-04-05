---
layout: post
title: Getting Started with Bricklayer-Lite
categories: [Getting Started]
tags: 
author: Betty Love
---

#### Topics on this page
{:.no_toc}
* TOC
{:toc}

Bricklayer-Lite is a app available at [bricklayer.org](https://bricklayer.org). Its purpose is to provide a gentle introduction to bricklayer programming. Programs are created by interactively selecting puzzle pieces that represent program elements and connecting them. This is all done in a browser window; hence no software download is required.  Only two-dimensional artifacts can be created with Bricklayer-Lite.

***

### Getting Started with Bricklayer-Lite Level_1 programming

Go to [bricklayer.org](https://bricklayer.org) and choose Apps -> Bricklayer-Lite. Take a few minutes to familiarize yourself with the contents of this page.  When you're ready to start creating your Level_1 program, click on "Level_1".

{% include image.html img="bricklayer-lite/bricklayer-lite01.png"  alt="Starting Bricklayer-Lite Level_1" %}

### Three elements of every Bricklayer and Bricklayer-Lite Program

Every Bricklayer and Bricklayer-Lite program contains the following three commands (lines of code / puzzle pieces)

   1. *open* statement - when you are getting started, the commands you use will be from Bricklayer Level_1; as you learn more, you'll start using functions from higher levels.  Currently, there are five levels of Bricklayer functions.  To open Level_1 in Bricklayer-Lite, first click on *open level*, then drag the *open Level_1* puzzle piece into the white part of the window pane, as shown below.

   {% include image.html img="bricklayer-lite/bricklayer-lite02.png"  alt="Bricklayer-Lite Level_1 open block" %}

{:start="2"}
   2. *build2D* statement - this command tells Bricklayer the dimensions of the virtual space you want to work in.  It should be at least as large as the artifact you plan to build.  Click on *build base plate* and then click on and drag the *build2D* puzzle piece into the area under the *open* puzzle piece.

   {% include image.html img="bricklayer-lite/bricklayer-lite03.png"  alt="Bricklayer-Lite Level_1 build2D block" %}

   Either at the same time you drag the *build2D* piece out or afterward, you want to connect it to the *open* piece as shown below.

   {% include image.html img="bricklayer-lite/bricklayer-lite05.png"  alt="Connect build piece to open piece" %}

{:start="3"}

   3. *show2D* statement - the third command that is in every Bricklayer-Lite program is the *show2D* command.  It is also the last command/statement. In Bricklayer-Lite click on and drag the *show2D* puzzle piece out, but don't hook it up yet.  We'll do that when we're done with the rest of the program.

   {% include image.html img="bricklayer-lite/bricklayer-lite04.png"  alt="Bricklayer-Lite Level_1 show2D block" %}

   The *"thing"* part of the show2D command is a way for you to name the artifact that you're creating. You can replace *thing* with any sequence of characters that you choose (or you can just leave it alone).  Note that you must keep the quotes around this sequence of characters. The name you choose has no effect on how the program runs or the artifact that it generates.

### Semicolons

Almost every Bricklayer command (line of code) should end with a semicolon.  There are some exceptions, but we will not consider those at this time. A semicolon tells the computer that the current command (or line of code) is done. In Bricklayer-Lite we must drag the semicolon puzzle piece from the *symbols* section and connect one to the end of each command.

{% include image.html img="bricklayer-lite/bricklayer-lite06.png"  alt="Bricklayer-Lite Semicolon" %}

After adding a semicolon to the end of each puzzle piece, your program should look like the following.

{% include image.html img="bricklayer-lite/bricklayer-lite07.png"  alt="Bricklayer-Lite 3-line program" %}

Selecting the semicolon puzzle piece for each statement can become tedious quickly.  It's possible to *duplicate* any puzzle piece by right-clicking on that piece and choosing *Duplicate*. If you have a mouse with two buttons, then right-clicking just means to click on the right button.  If you are using a Mac, then to right click on something you do a *Control-click*, which means you hold down the *Control* button and click. If you need more help on how to right-click on your machine, try google.

{% include image.html img="bricklayer-lite/bricklayer-lite08.png"  alt="Bricklayer-Lite duplicate block" %}

### Adding put2D function calls

Now we are ready to actually build our artifact.  In Level_1, the bricks available to us are as follows.

   - Sizes: 1×1, 1×2, 2×1, 2×2, 2×3, 3×2, 2×4, 4×2
   - Colors: BLUE, GRAY, BLACK, GREEN, RED, WHITE, YELLOW, EMPTY

The official documentation on Bricklayer Level_1 can be found at [bricklayer.org](https://bricklayer.org) by choosing *Apps -> Bricklayer -> Level 1 - Document*

For each size/color combination (how many of these are there?) a corresponding puzzle piece is available in the *function calls* section of the Bricklayer-Lite window.  The following image shows all the options for red bricks.

{% include image.html img="bricklayer-lite/bricklayer-lite09.png"  alt="Bricklayer-Lite Level 1 red bricks" %}

To put a 2x2 red brick at (0,0), drag the 2x2 red brick puzzle piece in to the pane with the other puzzle pieces.  Add a semicolon to it and connect the pieces as shown below.

{% include image.html img="bricklayer-lite/bricklayer-lite10.png"  alt="Bricklayer-Lite program" %}

### Running your Bricklayer-Lite program

At this point you are ready to run (execute) your program. So far you've just been building your program and the computer has not tried to execute any of the commands.  Now that we have a complete program, we need to tell the computer we're ready to run it.  To do this, click the *Run* button at the top of the white pane.

{% include image.html img="bricklayer-lite/bricklayer-lite11.png"  alt="Run a Bricklayer-Lite program" %}

If your program has no errors, output will appear in another pane on the same page. After running our sample program, I see the following.

{% include image.html img="bricklayer-lite/bricklayer-lite12.png"  alt="Output from running sample Bricklayer-Lite program" %}

This output is correct since we placed a 2x2 red brick at (0,0).  Since we set our *build2D* space to (2,2), our 2x2 red brick takes up the entire space.  Let's make our build space larger to get better perspective. The size area in the *build2D* puzzle piece is a dropdown menu. Click on it and choose (4,4) as shown below.

{% include image.html img="bricklayer-lite/bricklayer-lite13.png"  alt="Change build space size" %}

Now click on *Run* again.  The output should be as follows.

{% include image.html img="bricklayer-lite/bricklayer-lite14.png"  alt="Output from running sample Bricklayer-Lite program" %}

### Bricklayer code generation

One final note.  A little later on, you will graduate to writing Bricklayer programs in the Bricklayer app (an app you must download and install on your computer).  In it you type your commands as opposed to dragging and connecting puzzle pieces.  To help you get started understanding how your Bricklayer-Lite program corresponds to a Bricklayer program, when you run a Bricklayer-Lite program, the corresponding Bricklayer program is generated in the pane at the bottom of the Bricklayer-Lite page.  For our example, the Bricklayer program is as follows.

```
open Level_1;

build2D (4,4);

put2D_2x2_RED(0,0);

show2D "thing";
```

### Output format

One option in Bricklayer-Lite is the output format. The default is set to *PLAIN*.

{% include image.html img="bricklayer-lite/bricklayer-lite17.png"  alt="Bricklayer-Lite plain output format" %}

The other option is *LEGO* which can be selected from the drop-down menu.

{% include image.html img="bricklayer-lite/bricklayer-lite18.png"  alt="Bricklayer-Lite LEGO output format" %}

When we run our program with *LEGO* output format selected, we get the following.

{% include image.html img="bricklayer-lite/bricklayer-lite19.png"  alt="Bricklayer-Lite example with LEGO output" %}

### If you forget...

If you forget how to write a Bricklayer-Lite program, a quick way to refresh your memory is to look at an example. You can get to a Level_1 example quickly by clicking on *here* in the sentence at the top of the Bricklayer-Lite page.

{% include image.html img="bricklayer-lite/bricklayer-lite15.png"  alt="Bricklayer-Lite examples" %}

Now click on *Flag of Denmark*.

{% include image.html img="bricklayer-lite/bricklayer-lite16.png"  alt="Flag of Denmark example" %}

This will open up a Bricklayer-Lite program that generates the flag of Denmark.

### More information

For more information on Bricklayer Level_1 see [this post](/intro-to-level1-functions).  For more informaiton on both Bricklayer Level_1 and and programming in Bricklayer-Lite, see [https://bricklayer.org/level-1/](https://bricklayer.org/level-1/).
