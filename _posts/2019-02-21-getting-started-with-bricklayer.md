---
layout: post
title: Getting Started with Programming in the Bricklayer App
categories: [Getting Started]
tags: featured
author: Betty Love
---

#### Topics on this page
{:.no_toc}
* TOC
{:toc}

One can write Bricklayer programs in one of two ways:

   - Bricklayer-Lite is a web app available at [bricklayer.org](https://bricklayer.org) that provides a gentle introduction to bricklayer programming. Programs are created by interactively selecting puzzle pieces that represent program elements and connecting them. This is all done in a browser window; hence no software download is required.  Only two-dimensional artifacts can be created with Bricklayer-Lite. [This post](/getting-started-with-bricklayer-lite) discusses how to get started with Bricklayer-Lite.

   - The Bricklayer app is a text-based programming environment and any Bricklayer program can be created and run in the Bricklayer app.  The app must be downloaded and installed on your computer. Versions are available for mac and windows. This post will focus on getting started with programming in the Bricklayer app.


***

### Installing the Bricklayer App and an Artifact Viewer

Go to [bricklayer.org](https://bricklayer.org) and choose Apps -> Bricklayer -> Windows Download (or Mac OS Download).

{% include image.html img="bricklayer-app/bricklayer-app01.png"  alt="Download Bricklayer" %}

You will need to download and install the Bricklayer IDE as well as either LDD (LEGO Digital Designer) or LDraw.  The latter two are apps that Bricklayer uses to display artifacts created in a Bricklayer program. You will most likely need administrator access to install LDD or LDraw.

We recommend adding the Bricklayer app icon to your dock for easy access.

### Bricklayer app environment

The Bricklayer app window consists of two panes: one for your bricklayer program and one to view system (console) output when you execute your program.  You'll spend 99% of your time in the programming pane.

{% include image.html img="bricklayer-app/bricklayer-app02.png"  alt="Bricklayer Window" %}

You are ready to start typing your program.


### Three elements of every Bricklayer

Every Bricklayer program contains the following three elements:

   1. *open Level_n* statement - the "n" should be replaced with a level number. The number you choose depends on the Bricklayer functions you'd like to use in your program and what level they are in. Documentation for each of the five levels is available at [bricklayer.org](https://bricklayer.org).  Select Apps -> Bricklayer -> "Level n - Document" for Level x documentation.

   {% include image.html img="bricklayer-app/bricklayer-app03.png"  alt="Bricklayer documentation" %}

   For this example, I will use Level 3 functions, so will start my bricklayer program with the statement;

   ```
   open Level_3;
   ```
   Note that Bricklayer distinguishes between upper and lower case characters.  So if you type
   ```
   Open Level_3;
   ```
   or
   ```
   open level_3;
   ```
   your program will not run.  Also note the semicolon at the end of the statement.  You must include this or, again, your program will not run.


{:start="2"}
   2. *build2D (m,n)* statement - this command tells Bricklayer the dimensions of the virtual space you want to work in; m is the number of rows and n is the number of columns.  It should be at least as large as the artifact you plan to build.  I want to build a 32x32 work space, so will add the following statement to my program:
   ```
   build2D (32,32);
   ```
   Again note that case is important. Both
   ```
   Build2D (32,32);
   ```
   and
   ```
   build2d (32,32);
   ```
   will cause errors and your program will not run.



{:start="3"}

   3. *show2D "whatever"* statement - the third command that is in every Bricklayer program in Levels 1 through 3 is the *show2D* command.  It is also the last command/statement.  "whatever" is a name that you make up for the artifact that you're creating. You can place any sequence of characters that you choose between the double quote marks.  Note that you must keep the quotes around this sequence of characters. The name you choose has no effect on how the program runs or the artifact that it generates.  I'll use "demo" for this program, so will add the following line to my file:
   ```
   show2D "demo";
   ```

### Save your program!
You should save your program often so that you don't lose your work in case the power goes out or your computer decides to be weird.  You want to save your bricklayer code with a *.bl* extension.  The .bl tells your computer that this file is a bricklayer file.  Choose File -> Save from the Bricklayer menu or use your computer's shortcut key combination (Command + s for mac; Control + s for windows).  It's a good idea to stick with alphabetic and numeric characters in your file name.  Avoid spaces.  The hyphen or underscore characters are good choices too to help make the file name easily readable if it's long.  I've saved my file as *demo.bl*. Following is a snippet from the Bricklayer window.

{% include image.html img="bricklayer-app/bricklayer-app04.png"  alt="Bricklayer Program 0" %}

 Note that the blank lines are unnecessary, but are used to make code more easily readable.  The large number of lines between the build2D and show2D commands just indicate that I'm going to add more code there.


### Semicolons!!

Almost every Bricklayer command (line of code) should end with a semicolon.  There are some exceptions, but we will not consider those at this time. A semicolon tells the computer that the current command (or line of code) is done.

### Adding function calls

Following is the artifact that we will create with our Bricklayer program.  It is annotated to show the command needed for each of the blue, yellow, and green blocks.

{% include image.html img="bricklayer-app/bricklayer-app05.jpg"  alt="Level 3 Artifact" %}

In general the command
```
put2D (a,b) COLOR (x,z)
```
places a brick of color COLOR and size a x b at location (x,z).  So the commands
```
put2D (5,2) BLUE (0,0)
```
places a 5x2 blue block at location (0,0).

Our complete program is shown below.
{% include image.html img="bricklayer-app/bricklayer-app06.png"  alt="Bricklayer Program 01" %}

### Running your Bricklayer-Lite program

At this point we are ready to run (execute) our program. First let's save it.  Now click the *Run* button at the bottom of the Bricklayer window.

{% include image.html img="bricklayer-app/bricklayer-app07.png"  alt="Bricklayer Run Button" %}

If your program has no errors and you have LDD (LEGO Digital Designer) installed properly, your artifact will open in LDD. Below is a screenshot from LDD (after some work to center and resize the artifact).

{% include image.html img="bricklayer-app/bricklayer-app08.png"  alt="LDD screenshot" %}


### Errors---they are unavoidable!

Suppose that the following was the program I ran.  Challenge for you---can you find the error in it?

{% include image.html img="bricklayer-app/bricklayer-app09.png"  alt="Bricklayer program with error" %}

After running this version of the program, LDD did not open.  Uh oh. Now my Bricklayer program has a ominous-looking green arrowhead surrounded by red at line 10.  This tells me my program has an error on or near line 10.  To learn more, I look at the console pane at the bottom of the window.  It tells me there is an "Error: unclosed string".  If you look carefully at line 10, you'll see that I did not close the quotes around the word "demo".  This is my problem.  Sometimes identifying the error is not so clear; Bricklayer's console provides more information for us.  See the image below for the sequence of steps I could have gone through to identify my error.

{% include image.html img="bricklayer-app/bricklayer-app10.jpg"  alt="Bricklayer Console Error Message" %}
