---
layout: post
title: "Wacnet 1.1.1 - Minor UI update"
author: CF
description: ""
category: 
tags: [bacnet, wacnet]
---
{% include JB/setup %}

[BIC Automation](http://www.bicautomation.com/) was kind enough to let
us know that for slow networks (MS/TP), the UI was a little confusing.
You could click on a device, but nothing would happen... until a few
seconds later.

This is true and absolutely **terrible** as far as UI is concerned.
The user should always know what's happening. Letting the user wonder
if we crashed while we go on the network fetch the necessary data is
just bad manners.

As such, we quickly added a progress bar into Wacnet. Nothing changed
except for this progress bar.

![Wacnet Progress bar](/images/wacnet-1.1.1-progress-bar.png "Wacnet Progress Bar")

As usual, jump [there](https://hvac.io/docs/wacnet) to download the
newest version. (Those of you on the mailing list have already
received a direct download link.)

Cheers!
