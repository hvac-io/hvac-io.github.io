---
layout: post
title: "Graphivac 1.1.1 - Iframes"
author: 
description: ""
category: 
tags: [BACnet, Graphivac]
---
{% include JB/setup %}

Over the past few months, we've silently pushed a few updates to Graphivac.
We now officially announces version 1.1.1, which brings a whole lot of useful features.


## Value Formatting
Values retrieved from a live BACnet network or from Vigilia are not
always 'display friendly'. Nobody wants to see "22.233333333333°C",
but on the other hand you might very well want to be able to see the
5th digit on a very small value. Well, you can now choose your own
value formatting. SI prefix, significant digits, localized
fixed-point currency, rounded percentage...

Check out [d3.format](https://github.com/d3/d3-format) to see all the possibilities.

## Inline Math Evaluation
We've encountered numerous cases where it would have been great to be
able to *change* the value. For example for units conversions. Well,
it's now possible to do so! Simply insert an equation between curly
brackets, like so : `{(@bac.present-value + 2) * 4}` (Given a
present-value of 10, this is the equivalent of [(10 + 2) * 4], which
evalutates to 48.)

## Font Configs + Inheritance
It is now easier than ever to select the particular font you want in
your drawings. Not only can you choose how to format your text fields,
you can do so in an inheritable way. This means that you can decide to
configure the text for a whole project, but overwrite this
configuration for particular cases.

Can you imagine the need to show something in <span style='font-weight:bold;font-size:1.4em;color:red;'> large, bold and red </span>?

![Font configs](/images/graphivac-111/graphivac-font-configs.png "Font Configs")


## Embedding Iframes
This is a big one!
You can now embed your drawings into other webpages using Iframe.
This means that your users/customers don't have to see all Graphivac's editing tools, but can rather see a particular drawing directly.
Embed in your own website, in your Wordpress pages, in your single page application... wherever you want!
We even added a small Iframe editor to help you configure everything.

Want to automatically fetch live BACnet data from Wacnet?
Want to change the fonts and colors to better match your own website's theme?
Want to automatically zoom the drawing to fill the space given to the Iframe?
![Iframe Editor](/images/graphivac-111/graphivac-iframe-edit.png "Graphicac Iframe Editor")

What does it looks like? Well, just take a look below.
No distracting editor and toolbar, simply a paneable, zoomable, HVAC drawing.
The perfect addition to please your users!

<iframe src="https://graphivac.hvac.io/o/public/p/P-cBZ5F9AJC3/g/G-WxOgldoJOj?iframe=t&init-zoom=t" height="400" width="100%" style="border: 1px solid #3365cc;"></iframe>
