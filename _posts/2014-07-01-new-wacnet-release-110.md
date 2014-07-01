---
layout: post
title: "New Wacnet Release: 1.1.0"
author: CF
description: ""
category: 
tags: [bacnet, wacnet]
---
{% include JB/setup %}

Hello folks!

We just released a brand new version of Wacnet.

You can download it here:
[Download Wacnet](https://hvac.io/docs/wacnet)


<video autoplay="autoplay" class="well" controls="" loop=""width="100%"> <source src="/videos/wacnet-1.1.0.webm" type="video/webm"> <source src="/videos/wacnet-1.1.0.ogv" type="video/ogg"> <source src="/videos/wacnet-1.1.0.mp4" type="video/mp4">Your browser does not support the video tag.</video>
	

## New UI

This version brings a complete revision of the UI, which makes it far
easier to work with.

The new UI shows more information. In fact, all the objects 'basic'
info can be seen directly by selecting a device.

We show:

- The object name
- The description
- It's current value
- The unit

If this isn't enough, we also provide a way to get pretty much all the
BACnet data of an object by clicking this little button:

![Details button](/images/wacnet-1.1.0-release-details-btn.png "Details button")

You should then see a little popup window showing you all the info you
need:

![Details popup](/images/wacnet-1.1.0-release-details-btn2.png "Details popup")



We made the UI nearly identical than Vigilia (the data
logging service), which will be more convenient for users of both.

![Wacnet UI](/images/wacnet-1.1.0-preview1.png "Wacnet UI")

![Wacnet Filtering Box](/images/wacnet-1.1.0-preview2.png "Wacnet Filtering Box")


## Trend Logs Download

We also added the ability to download BACnet trend logs directly to
CSV files by simply clicking on the download button.

![Download Trend Logs](/images/wacnet-1.1.0-preview3.png "Download Trend Logs")

Here's what the file looks like when opened in a spreadsheet:

![Trend Logs Into CSV](/images/wacnet-1.1.0-preview4.png "Trend Logs Into CSV")


## Web API

All the data consumed by the UI comes from the API. This means that
if you don't like our interface, you can make your own!

If you are more on the technical side, you can also make shell scripts
to retrieve limited information.



## Vigilia Integration

Finally, we've integrated Vigilia (the data logging service)
into Wacnet.

If you are subscribed, you will have the ability to directly
look at your logs without even leaving Wacnet. Simply press a little
button besides the object name and you'll see a graph pop out:

![Vigilia button](/images/wacnet-1.1.0-release-vigilia-btn1.png "Vigilia button")

![Vigilia button](/images/wacnet-1.1.0-release-vigilia-btn2.png "Vigilia button")


## Moving forward

As usual, if you need some new features, tell us and we'll take them
into considerations for a future release.
