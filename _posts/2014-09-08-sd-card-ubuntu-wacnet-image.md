---
layout: post
title: "SD card: Ubuntu Wacnet image"
author: CF
description: ""
category: 
tags: [Wacnet, Bacnet]
---
{% include JB/setup %}

![SD card](/images/SD-card.jpg)

We've just prepared a Ubuntu 12.04.4 and Wacnet 1.1.2 image and decided to make it
available to everyone, for free.

Here's the download link:
[MK802iv Wacnet image](https://drive.google.com/file/d/0B2TVfibKf7NGTU96QktDbS1qeFk)

This SD card image (8GB) is to be used with the MK802iv miniature PC:
![MK802iv (image from liliputing.com)](/images/mk802-iv-le_02.jpg)

If you need admin power:

- User: hvacio
- Password: hvacio

The PC will announce itself as **HVAC** on the LAN, which makes it
easy to find by looking on a router at the list of all connected
devices.


# Automatic Wacnet launch

Wacnet is programmed to be launched as soon as the mini PC is plugged
into a power outlet.

After a few seconds, you can go to http://*the-mini-pc-IP*:47800 and
see the same web interface you would see if you launched Wacnet on
your own machine.


<video autoplay='autoplay' class='well' controls='true' loop='true' width='100%'><source src='/videos/wacnet-1.1.0.webm' type='video/webm'><source src='/videos/wacnet-1.1.0.ogv' type='video/ogg'><source src='/videos/wacnet-1.1.0.mp4' type='video/mp4'>Your browser doesn't let you see the video... fear not! To see the BACnet Explorer video, click <a href='/videos/wacnet-1.1.0.webm'>here</a>.</video>



# SSH (mostly) Disabled

For all intended purposes, SSH has been disabled. No login/password
will be accepted. The only possible connection is with a private key
that only we, **HVAC.IO**, possess.

As such, if you want to play around in Ubuntu and change some configs,
you'll have to plug a monitor and a keyboard to the mini PC. At this
point, you'll be able to re-activate SSH access if you so desire.

By doing this, we make sure that nobody will accidentally leave a
vulnerable SSH access, while still being able to provide some kind of
support, if necessary.

(You can obviously remove our public key from the SSH access if you
don't like the idea of us being able to connect to the device.)


# SD Preparation

1. Extract the compressed image (In the 7z format; you
   might have to download an application to decompress it);
2. Copy the image `mk802iv.img` to an SD card (minimum 8GB),
   
On linux, you can use this command (just replace `/dev/sdc/` by
whatever is your SD card... probably `/dev/sdb`):

	sudo dd bs=4M if=mk802iv.img of=/dev/sdc

On Windows, you can download DD for Windows
[here](http://www.chrysocome.net/download), or
[Win32DiskImager](http://sourceforge.net/projects/win32diskimager/).
Please note that we haven't tested any of those, but they appear to be
the ones most often used to copy an image to an SD card.


# Testing

The MK802iv should boot on the SD card instead of its own Android
software. The easiest way to validate that everything works is to plug
a monitor to the device and make sure it boots into Ubuntu, *not*
Android.


If it does, congratulation, you now have your own BACnet webserver
that you can hold in your hand!
