---
layout: post
title: "A Killer Feature With HVAC Wiki and 10 lines of code"
author: CF
description: ""
category: 
tags: [wiki, Vigilia]
---
{% include JB/setup %}


[Earlier this month](http://blog.hvac.io/2015/07/11/launching-hvac-wiki/) we launched [HVAC Wiki](https://wiki.hvac.io).

We are happy to see that many people contributed, and hope this is
only the beginning.

But, as the saying goes, "put your money where your month is". Less
than one month after launching HVAC wiki, we have already incorporated
the HVAC Wiki inside [Vigilia](https://hvac.io/services/vigilia) and
created what you could call a 'killer feature'. Okay, it might be over
the top, but we needed a nice title. ;-)

As you may well know, devices on a BACnet network provide information
about their vendor and their model.

By the way, if you are using [Wacnet](https://hvac.io/docs/wacnet),
you can get this information via the explorer, or with the following
command:

{% highlight clojure %}
(bacure.core/remote-object-properties 1234 
                                      [:device 1234] 
                                      [:vendor-name :model-name])
{% endhighlight %}

Anyhow... Seeing the device's model can be useful, but it still leaves
the task of finding the information entirely to the user.

How can you upgrade the device? Make backups? Is there known issues?
Compatible devices? Everything needs to be rediscovered from scratch
by every user.

You could potentially contact the vendor, but once your network has
devices from more than 2 or 3 vendors, you'd which all the info was at
the same place. In addition, if you are no longer in business with the
vendor, you might find it a little harder than usual to go get
important information...

What you'd really need is... a wiki!

The new killer feature is really, really simple. In Vigilia, we look
at the device vendor/model and make links directly to the wiki. This
way, you are always 1 click away from the information you seek.

[![Vigilia - HVAC-wiki](/images/vigilia-hvac-wiki/vigilia-hvac-wiki.png)](/images/vigilia-hvac-wiki/vigilia-hvac-wiki.png)

This is the kind of nifty things that can be added basically for free
in any application, and we invite you to do it!

The beauty of a wiki is that its usefulness grows with the number of
users.
