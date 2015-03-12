---
layout: post
title: "Introducing Virtual Objects"
author: CF
description: ""
category: 
tags: [Vigilia]
---
{% include JB/setup %}

In the last post, we started explaning how our harmonized timeseries
worked.

We can now introduce and explain the brand new **Virtual Objects**.

Virtual objects are objects that can be created by using other
(real or virtual) objects.

It's clear, isn't it?

No?

Okay, let's say you have a hot water system. You recorded the
temperature going in, the temperature going out and the flow.

As any engineering student will tell you, this is all you need to
calculate the power consumption of the system.

![img](/images/harmonized/virtual-obj.svg)

So, how would you approach this if you wanted to study the power
consumption? 

If you catched the system early enough you could have created a
variable (updated by the BAS programs) and then record it.

    Power_analog_variable = (Temp-1 - Temp-2) * Flow

There are 3 problems with this approach.

First, controls are much more proprietary than most of us would like.
Even by knowing well in advance you might need this variable, there's
no guarantee you will be able to create it.

Second, creating variables for every single "maybe I'll need this..."
would take way too much time.

Finally, in a project spanning years, you WILL make some mistakes when
creating the variables, or simply forget to create some of them.

Thankfully, with virtual objects, the need for a complicated and
extensive preparation disappears overnight.

You don't need to know in advance what you'll want to observe. As long
as you recorded enough fundamental data from the sensors, you can
recreate any object you want.


If you've
[read](http://blog.hvac.io/2015/03/10/harmonized-timeseries/) the last
post on how our hamonized timeseries were sanitized, it should be easy
to understand how we can robustly handle virtual objects, as shown in
the picture below:

![img](/images/harmonized/harmonized-virtual.svg)

If you look closely, you'll see that virtual objects return timeseries
in exactly the same format as the harmonized timeseries by which they
are created. This is no accident: for any consumer of our harmonized
timeseries, virtual objects are indistinguishable from real objects.
This means that all the existing tools will work just as well with
those brand new virtual objects!

See this capture of our *Analytics* tabs. One of these objects is virtual:
![img](/images/harmonized/dimentional-virtual.png)

The same object in the *Timeseries* tab (green line):
![img](/images/harmonized/virtual-timeseries.png)

This object was never recorded (It doesn't even really exist). It was
created months after the recording, and yet we can use it as if it was
there all along.

By this point, you should start to see how these virtual objects can
save you a whole lot of time, while multiplying the usefulness of
Vigilia as a whole.

If you find surprising ways in which these virtual objects save you
time, please let us know, we always love to hear stories from our
users.
