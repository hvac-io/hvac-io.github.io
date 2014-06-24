---
layout: post
title: "BACnet Network Profiling with Wacnet"
author: CF
description: ""
category: 
tags: []
---
{% include JB/setup %}

One of the most underused Wacnet feature is the REPL, which gives
access to a complete programming environment. I suppose this shouldn't
be surprising, as learning a new language is always a time consuming
endeavour.

In case you don't know where the REPL is, it's in the REPL section of
Wacnet:

![Wacnet REPL](/images/wacnet-repl.png "Wacnet REPL")

While learning from scratch is probably not possible for everyone, one
can easily share little snippets to be used in the REPL. Just like an
Excel macro, or an AutoCAD script, you don't have to be able to write
it.


The following code will export a text file containing a rudimentary
profile of the BACnet network.

{% gist Frozenlock/bb26994acd4f2665d557 %}

And when we open the `network-profile.txt` file:

{% gist Frozenlock/791d2e3e53d8abad3dd2 %}

Neat, right?
With a few lines of code, you generated a summary of all
the devices, their model and from which vendor they originate.
