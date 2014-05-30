---
layout: post
title: "What's Coming in Wacnet 1.1.0"
author: CF
description: ""
category: 
tags: []
---
{% include JB/setup %}

For the last few weeks we've worked hard to improve the underlying
BACnet library of Wacnet. If everything goes according to plan, a new
version of Wacnet should see the light of day pretty soon.

## Bug fixes

There's many little code improvements and some bug fixes.

Speaking of bugs, the guys at Schouten Techniek discovered one when
devices used proprietary engineering units. This is now fixed and will
be integrated in the next release. Thanks guys!

Remember, if you find bugs, please report them to us! We don't have
the power of telepathy yet... we can't know what you don't tell us!

## Open Source UI

We are currently in the process of making parts of Vigilia's
user interface open source and integrating it into Wacnet.

![Wacnet UI](/images/wacnet-1.1.0-preview1.png "Wacnet UI")

It features a much better way of selecting controllers and gives you a
nice filtering box to quickly select the objects you want.

![Wacnet Filtering Box](/images/wacnet-1.1.0-preview2.png "Wacnet Filtering Box")

## Web API

All the data consumed by the UI comes from the API. This means that
if you don't like our interface, you can make your own!

If you are more on the technical side, you can also make shell scripts
to retrieve limited information.

## Trend Logs Download
We also added the ability to download BACnet trend logs directly to
CSV files by simply clicking on the download button.

![Download Trend Logs](/images/wacnet-1.1.0-preview3.png "Download Trend Logs")

![Trend Logs Into CSV](/images/wacnet-1.1.0-preview4.png "Trend Logs Into CSV")

## Vigilia Integration
Finally, we've integrated Vigilia (the data logging service)
into Wacnet.

If you are subscribed, you will have the ability to directly
look at your logs without even leaving Wacnet. Simply press a little
button besides the object name and you'll see a graph pop out:

![Vigilia Into Wacnet](/images/wacnet-1.1.0-preview5.png "Vigilia Into Wacnet")

## Tell Us What You Want!
We hope you'll like all these new features.

While we can try to guess other users want by solving our own needs,
this can only take us so far. If there's a feature you'd like to see
added, please tell us!

Cheers!
