---
layout: post
title: "Network Discovery with Devices Ignoring WhoIs"
author: CF
description: ""
category: 
tags: [bacnet, wacnet]
---
{% include JB/setup %}

Here's a little something that happened to me and shows how
incredibly powerful Wacnet's REPL is when you need something that
isn't already programmed in the software.

![Wacnet REPL](/images/wacnet-repl.png "Wacnet REPL")

We recently were tasked to use Vigilia to record a subset of a BACnet
network. The only thing we knew was that many devices were MS/TP, that
the network was composed of multiple buildings, and that we had a few
dozen devices to record with IDs between 20000 and 20999.

Up to this point, everything is pretty standard and can easily be
handled just by firing up Wacnet.

As I did countless time before, I started Wacnet and scanned the
network. I sent a `Who-Is` broadcast, expecting to see the devices I
was looking for. Plenty of devices answered, but not those I was
looking for. In fact, in the 20xxx range, less than 5 answered.

It's not surprising that a few devices fail to answer with the `I-Am`
broadcast, especially in congested networks. One can usually just wait
a few minutes/hours and all the devices will have announced
themselves. But not this time.

On this particular case, I had to wait for **days** to come clause to
the number of devices I was expecting.

This was simply ridiculous. Nobody is going to wait a week after you
start a software before seeing any effect.

But the problem remained... the devices were ignoring (or couldn't
answer) my `Who-Is` request. Nasty situation...

I talked about my situation on the BACnet mailing list. While there's
multiple possible causes, there's a hacky solution that should work
for most of them.

Mr. Hartman from Trane summarizes the problem quite well:

> (...) broadcasts can and will get lost, especially when there are a
> lot of them. If you broadcast a Who-Is with no parameters, ALL
> devices have to answer, so you will get a flurry of I-Am, some of
> which may get dropped.

To discover the devices I'm looking for, I have to minimize my network
usage and send a ranged `Who-Is`.

I'll do more than that: I will send a `Who-Is` *for a single device*.
This way I make sure there's absolutely no network congestion.

Here is where Wacnet's REPL shines: Without the need to recompile
anything, I can make new functions on-the-fly.

Wacnet is using the function
[find-remote-devices](http://frozenlock.github.io/bacure/bacure.remote-device.html#var-find-remote-devices)
to send the `Who-Is` broadcast. Here's the new function targeting a
single device:

{% gist Frozenlock/f6d3226e6149fe6be1d0 %}

And then a little function to scan IDs within a range using this method:

{% gist Frozenlock/cd48827ecea636dd110c %}

After that, all I had to do was to enter `(scan-range 20000 20999)`,
wait around 3 minutes and I had the **complete** devices list.

No need to recompile or download any additional widget; I could create
my own function directly when and where I needed it.
