---
layout: post
title: "Bringing the Internet to a Separate Controls Network"
author: CF
description: ""
category: 
tags: [Vigilia, Bacnet, Internet]
---
{% include JB/setup %}

We recently had to do a couple of jobs with Internet-less controls
network and thought we could explain how we are doing it.

# Internet-less Controls Network

Security wise, it's a good idea to make sure your controls network is
*not* connected to the Internet.  In fact, it's best if you can put it
on its own VLAN, completely separated from the other networks.

Knowing this, it's not really a surprise to see this kind of
configuration in the wild, especially with universities, hospitals and
large factories.

But wait, does this mean [Vigilia](https://hvac.io/services/vigilia)
is completely useless for them and we can't use it exactly where it
would be incredibly useful?

(Dramatic pause)

Of course not! ;-)

You can use Vigilia with those as well, you just need to bring the
Internet to the recording device.

Don't be scared, it's quite painless and can most of the times be done
without any configurations. As we'll see next, it's literally
plug-and-play.


# Bringing the Internet

Okay, so let's first check how you would usually connect a computer
(or a mini computer) to your controls network when it has Internet:

![Vigilia wiring combined network](/images/network-combined.png "Combined networks")

In this case, you only need to plug the Ethernet cable that gives
access to your controls network AND the Internet.

Now, what if those two things are separated?
In that case, we need to plug 2 cables. Thankfully, this is really
easy. Just plug a USB to Ethernet adapter and you have another
Ethernet interface ready to accept the second wire:

![Vigilia wiring separated network](/images/network-separated.png "Seperated networks")

**That's it**

We told you it was plug-and-play!

You didn't even have to deal with the IT department!
(But you really should let them know what you are doing.)

With this configuration, Vigilia will record the BACnet network from
one wire, compress and encrypt the data, and then send it on the other
one to be safeguarded and made available as a read-only resource on
our servers.

And remember, in these images we show you a mini PC, but it could just
as easily be a full size desktop computer.

