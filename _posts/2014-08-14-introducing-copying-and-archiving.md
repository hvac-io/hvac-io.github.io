---
layout: post
title: "Introducing Copying and Archiving"
author: CF
description: ""
category:
tags: [Vigilia]
---
{% include JB/setup %}

We are happy to announce a new feature for all our Vigilia users:
You can now create copies of your projects.

As our current users know, when a given project has reached its
capacity, it will delete the oldest logs when new ones are inserted.

This is the behavior you would expect, as often you only need the last
months/year of HVAC historical data.

## Use Cases
However, there are cases where you do want to keep the logs for a long
time.

Say, for example, the first year of a system that you intend to
upgrade in the following months, or when an energy efficiency firm
needs to do a before/after analysis.

Keeping 5 years of data just to be able to compare the first year with
the fifth would be a little wasteful.

There are also the litigious cases where a problem occurred, but the
culprit has yet to be found. In this case, it's safer to make sure to
keep all the data for this period.


## How it works
You can create a copy of your project simply by pressing the 'copy'
button. You will be asked for a name of the new copied project.
Immediately after, all the data from the source project will be copied
into the new one.

Here I created a new project with the name 'Hospital (copy)'. After a
few seconds, all the 2382 objects and their logs were copied into the
new project.

![Copy Project Button](/images/copy-archive-1.png "Copy Project Button")

![Project Copied](/images/copy-archive-2.png "Project Copied")


## Archiving

There's no link between the data of the 2 projects. This means that
even if you delete one of them, the other will remain exactly as is.

Unless you configure the copy to receive logs from our logging
software, it will remain unchanged forever.


Hope you'll enjoy this feature!
