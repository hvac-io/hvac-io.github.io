---
layout: post
title: "Harmonized Timeseries"
author: CF
description: ""
category: 
tags: [Vigilia]
---
{% include JB/setup %}


At scale, every little detail is there to get you. 

In this post, we describe why and how we harmonize the timeseries
before using them.

## Timeseries Gotchas

When trying to analyze timeseries, there's few thing that one must
be careful about. If you are dealing with big systems, chances are
you will encounter all of them at the same time.

- Different timestamps;
- Different time intervals;
- Irregular time intervals;
- Missing values (communication error, power outage).
    
Each of these is a pain. They waste precious time and some can even
cause programs to crash. How do you deal with that?

## Harmonizing

For Vigilia, we decided to implement a special engine to
automatically harmonize timeseries. Here's a simplified
representation of how it works:

![img](/images/harmonized/harmonized-opt.svg)

We take the source timeseries and find the closest values from a
timestamp to generate the new harmonized timeseries.

We make sure to discard any time with missing values (Nil, NaN&#x2026;)
from communication errors or power failures. This means that any
tool using our harmonized timeseries can be sure we will never send
anything else than numbers.

We abstract away to low level dirty stuff and provide a crisp, clean
timeseries simple to manipulate.

## Representative Spread

Contrary to some simpler database queries, which return 'random'
samples, our harmonized timeseries will automatically spread the
timestamps on the entire time allocated. For example, if you ask for
50 points within 10 days, the first day will be composed of 5
points.

(This is how our Timeseries tab 'zooms-in' on different time
periods. Harmonized timeseries are created on-the-fly to fit
into the required time period.)

![img](/images/harmonized/harmonized-sampling.png)

## Instant Access to Harmonized Timeseries

You don't need to use our API to get your hands on harmonized
timeseries. You can simply take a look in the Analytics tabs. We
already give you the timeseries in a convenient representation,
ready to be exported in the formats of your choice.

![img](/images/harmonized/harmonized-table.png)


Furthermore, you can use the graphical selection tools on the same
page to filter out unwanted data.


![img](/images/harmonized/harmonized-selection.png)

## Building with Harmonized Timeseries

Our harmonized timeseries engine makes it much easier to work with
large quantity of data accumulated in real-world (messy, unreliable)
conditions.

The reason we take the time to do a brief overview of our harmonized
timeseries is because we used the incredible convenience they offer
to make yet another tool.

We are truly excited by this new tool. In fact, it's probably the
biggest game changer in the field since we introduced the
dimensional analysis last year!

We will, in the next few days, describe how it works and the
tremendous advantages it offers.

By the way, we already added the tool to Vigilia. You might find it
if you search deep enough&#x2026; it's truly 'magical'.
