---
layout: post
title: "BACnet Tablets?"
author: CF
description: ""
category: 
tags: [bacnet tablet wacnet]
---
{% include JB/setup %}

We decided right of the bat to make the open source
[Wacnet](https://hvac.io/docs/wacnet) run on the JVM. While it might
have looked like it was going to chain us to powerful computers only,
we knew what we were doing. The trend was already quite clear:
processing power getting cheaper every day.

This means that we can develop something right now for devices that
seem prohibitively expensive, but knowing that in 18 months they'll be
twice as cheap.

We dabbled into some architectures a little different from your
classic PC by running Wacnet on the Raspberry Pi and the MK802. The
process was surprisingly straightforward: find a compatible linux
distro (that's the hardest part), install the correct JVM and tada!
You can now run the BACnet Webserver directly on these miniature
computers.

![RaspberryPi Model B](/images/raspberry-pi-model-b-300x225.jpg "RaspberryPi Model B")

Following the processing power price curve, we can expect that these
will soon be expandable. In fact, in many cases, they already are.
It's often cheaper to just buy a preconfigured unit than taking the
time to install the software on a normal PC and configuring it
yourself.

The next devices to become disposable are probably the tablets. This
is very exciting, because it means that you can bundle your
application with some kind of user interface. This enables you to give
immediate feedback to your user, but also to broaden your customer
base, because now they don't need to know how to SSH into a remote
machine!

![Android tablet](/images/bacnet-tablet.JPG "A future Bacnet tablet?")

In light of this, we are already preparing ourselves to install Wacnet
on tablets. A complete standalone Bacnet webserver on a disposable
tablet... connect it to any network and you can see the entire
network. This would enable technicians to be directly in front of
their machines AND access the network at the same time.

We are not quite there yet, but we are getting close. We are exploring
the different chip architectures and trying to find which one is going
to be cheap and around for a little while. There's also other things
to consider, such as the screen size. What is the correct size to
enable you to see enough information, but which isn't a hassle to
bring along?

We'll let you know here and on the mailing list when a prototype is
ready. Until then, feel free to tell us what feature you'd like on a
BACnet tablet!

<form action="https://hvac.io/newsletter" class="form-inline" method="POST" role="form">
	<div class="form-group">
	    <input class="form-control" id="email" name="email" placeholder="mike@acme.com" required="" type="email">
			<input type="hidden" name="source" value="Blog">
	</div>
	    <button class="btn btn-default" id="submit-btn" type="submit">
			<span class="glyphicon glyphicon-envelope"></span> Stay informed!</button>
</form>
