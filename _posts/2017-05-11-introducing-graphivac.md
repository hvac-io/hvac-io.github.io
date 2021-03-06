---
layout: post
title: "Introducing Graphivac"
author: CF
description: ""
category: 
tags: [BACnet, Graphivac]
---
{% include JB/setup %}

![Graphivac Snapshot](/images/introducing-graphivac/graphivac-snapshot.svg "Graphivac Snapshot")
<p class='text-center'><b>Try it <a href="https://graphivac.hvac.io/#/o/public/p/P-cBZ5F9AJC3" target="_blank">online</a>!</b></p>


Graphivac is a new tool to make BAS Graphics. While on the surface it
may look similar to other software you've already seen, the underlying
architecture is quite different, which gives it huge advantages.

Many BAS Graphics software are built around images. You place
different images on a canvas and try to represent HVAC systems as best
as you can. One downside of this approach is how dependent on the
images themselves you are. Let's take a look at the picture below :

![Orcaview misaligned images](/images/introducing-graphivac/orcaview-misaligned.png "Orcaview misaligned images")

The software is *blind* to what you are doing. It doesn't know that
ducts are supposed to touch. Or that a gap between images might be
undesirable.

With Graphivac, we took an approach that is much more powerful and
flexible. When the user add an object, we don't store an image; we
store *what* and *where*. The image is simply a visual representation
of what is there.

This allows us to handle trivial matters like making sure there is no
gap between duct sections.

![Graphivac Simple Duct](/images/introducing-graphivac/graphivac-duct.png "Graphivac Simple Duct")

It also means you can change the visual representation of a system
without re-drawing it; selecting a different *theme* is enough. In
other words, you can upgrade the style of **all your existing
drawings** in a single step. Incredibly useful when you want to give a
breath of fresh air to your company's image.

In addition, it's possible to leverage drawings to build relations
between physical components and use this to make advanced analysis.
(More on this later.)


## Built for Browsers

Many software will give you the option to 'export' into a web format.
The exporting process will often do a good-enough job, but will still
be very limited in what is possible to do. With Graphivac, the editor
itself is built for the web. No more surprises between the editor and
the viewer. What you see is what you get.

We leverage the SVG (Scalable Vector Graphics) format supported by all
major browsers to render crisp and zoomable drawings of HVAC systems.

## Unlimited Canvas

Contrary to many BAS graphics software, Graphivac's engine allows you
to pan and zoom as much as you want. You don't have to divide big
systems into smaller drawings just so that they can fit; they will
always fit!

![Panning and zooming](/images/introducing-graphivac/pan-zoom.gif "Panning and zooming")

<div class='text-center'> <i>The canvas is infinite. You don't have to split systems into smaller drawings anymore.</i></div>


## Extensible : Modes

Graphivac is built to make it easy to add new features and
capabilities. The main way to do this is via 'modes', each of which
can give different options and tools to the users.

The 3 built-in modes in Graphivac are a good example :

	- Editor : draw HVAC systems;
	- Live : See live data from a BACnet network directly on the drawing;
	- Historical : Replay historical data on the drawing.
	
This approach allows Graphivac to be extended to work with your
favorite existing tools.

![Graphivac Historical Mode](/images/introducing-graphivac/historical-mode.gif "Graphivac Historical Mode")

<div class='text-center'> <i>Historical Mode</i></div>

## Metadata and Structure

We mentioned a little earlier that Graphivac's underlying architecture
gave it many advantages, notably the possibility of building relations
between components. This is because we know *what* is *where*.
Consequently, we know which component comes before the next.

![Generating Relations](/images/introducing-graphivac/graphivac-relations.png "Generating Relations")


## Download and Documentation

For professional usage, you want might want to use your own Graphivac Server.
A free server is available for download on [HVAC.IO](https://hvac.io/products/graphivac).

Detailed documentation about Graphivac usage can be found on the HVAC wiki.

<div class='text-center'>
  <a href='https://wiki.hvac.io/doku.php?id=suppliers:hvac.io:graphivac'>
    <img width='300px' src='/images/introducing-graphivac/hvac-wiki-logo.png'>
  </a>
</div>

Enjoy!
